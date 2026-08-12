# Composition Gate Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** dependency_lens + loadout_checker → Composition Proof Pipeline

## Purpose

Verify that a skill's dependencies exist in the loadout BEFORE installation. This prevents the composition gap that caused `dependency_gatekeeper_recipe` to fail the gate — by catching missing deps at composition time, not post-installation.

## The Problem This Solves

The deity rule `[dependency_proof_before_loadout]` states:
> "A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation."

But the verification happens AFTER install. This recipe provides a PRE-flight check:
1. Parse the skill's declared dependencies
2. Verify each dependency exists in loadout
3. Report any gaps before they cause a gate revert

## Ingredients

1. **Dependency Lens** (`crafted/dependency_lens.md`) — Extract dependencies from skill metadata
2. **Loadout Checker** — A simple bash script that verifies files exist in loadout dirs

## Pipeline Stages

### Stage 1: Dependency Extraction (via dependency_lens)

For the target skill:
1. Read the skill file
2. Extract `Composes:`, `Ingredients:`, `Requires:`, and import statements
3. Normalize to a list of required skills
4. Identify declared type (e.g., "lens", "recipe", "towering")

Output: List of required skills with their expected locations

### Stage 2: Loadout Verification

For each extracted dependency:
1. Check `/tmp/df-dev-gv4sl7u7/dev-1/agents/agent_001/.claude/skills/`
2. Check `/tmp/df-dev-gv4sl7u7/dev-1/agents/agent_001/crafted/`
3. Check `/home/runner/work/dark-factory-live/dark-factory-live/.claude/skills/`
4. Report status: FOUND / MISSING / PARTIAL

### Stage 3: Composition Proof

Generate a proof certificate:

```json
{
  "target_skill": "<skill_path>",
  "dependencies": [
    {"name": "<dep>", "expected_path": "<path>", "status": "FOUND|MISSING"}
  ],
  "proof_status": "COMPOSITION_PROVEN | COMPOSITION_GAP | COMPOSITION_UNVERIFIABLE",
  "gate_recommendation": "INSTALL | HOLD | REJECT",
  "gaps": ["<list of missing deps>"],
  "timestamp": "<iso>"
}
```

## Quality Gate

- [ ] At least 3 loadout paths checked
- [ ] All declared dependencies verified
- [ ] MISSING dependencies documented with expected paths
- [ ] gate_recommendation matches proof_status (no mismatches)

## Why Epic

- Composites a lens with a system checker (non-obvious combination)
- Addresses a real, documented deity rule gap
- Prevents the exact failure mode that cost fitness in previous cycles
- Generates actionable output (gaps are fixable, not just reported)

## Usage

```bash
# Apply to any skill before installing
1. Identify the target skill path
2. Apply Stage 1 (dependency_lens)
3. Apply Stage 2 (loadout verification)
4. Generate Stage 3 proof
5. If COMPOSITION_GAP: fix gaps BEFORE listing for trade
```
