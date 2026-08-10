# Dependency Gate Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** dependency_lens (crafted) + structural pattern matching

## The Problem

A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation. The dependency_audit_lens discovered chain_verifier_recipe's missing Divergence/Convergence Lens after install — the revert still hit. Audit tools catch failures; they don't prevent them.

## Ingredients

1. **dependency_lens** — Trace imports, references, and causal chains between skills
2. **Loadout scanner** — Verify referenced skills exist in loadout directory
3. **Proof generator** — Produce evidence that all dependencies are satisfied

## The Protocol

### Step 1: Extract Dependency Claims

Parse the skill file and identify all skill references:

- `Composes:` sections listing other skills
- `Ingredients:` lists from recipes
- Import statements or file path references
- Skill type labels (e.g., "lens", "recipe") that imply dependencies

Output: `dependency_claims = ["skill_name_1", "skill_name_2", ...]`

### Step 2: Verify Each Dependency Exists

For each claimed dependency:

1. Check if it exists in `loadout/` directory
2. Check if it exists in `crafted/` directory
3. Check if it exists as a known skill type in `.claude/skills/`

Output: `dependency_verification = [{name, found: bool, location, proof}]`

### Step 3: Generate Proof Report

```
## Dependency Gate Report for [skill_name]

### Total Dependencies: N
### Found: M
### Missing: K

### Proof Chain:
| Dependency | Status | Location | Evidence |
|------------|--------|----------|----------|
| skill_1 | ✓ FOUND | loadout/skill_1.md | file exists |
| skill_2 | ✗ MISSING | - | - |

### Gate Decision: [PASS / FAIL / PARTIAL]
### Recommendation: [LIST / REVISE / BLOCK]
```

## Quality Gates

A skill PASSES the dependency gate when:
- All listed dependencies are found in loadout OR crafted
- No dependencies are missing that would cause runtime errors
- Proof report includes specific file paths for verification

A skill FAILS when:
- Any `Composes:` skill is missing from loadout
- The skill references a skill type without that skill existing
- The skill would import something that doesn't exist

## Why This Recipe Is Valuable

- **Prevents the chain_verifier_recipe problem** — catches missing Divergence/Convergence Lens before install
- **Improves fitness** — dependencies resolved upfront means fewer reverts
- **Satisfies dependency_proof_before_loadout rule** — explicit proof that dependencies exist
- **Rare rarity** — the only recipe that explicitly addresses the dependency verification requirement

## Usage

```bash
# Before listing a skill that composes others
1. Read the skill file
2. Apply this recipe to verify all dependencies exist
3. If PASS → safe to list
4. If FAIL → add missing dependencies first
```

## Connection to Standing Rules

This recipe directly enforces:
- **dependency_proof_before_loadout**: "Loadout admission requires dependency resolution"
- **preflight_verifier_improves_fitness**: "Skills that verify chains before gate submission improve fitness"
- **gate_listed_not_gate_passed**: "Verify composition works end-to-end BEFORE declaring it loadout-ready"
