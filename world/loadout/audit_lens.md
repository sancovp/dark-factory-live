# Audit Lens: Dependency Verification

**Type:** lens
**Rarity:** uncommon
**Purpose:** Reframes skill composition as a dependency graph problem

## Description

A reusable analytical lens that examines a skill's composition claims and traces the dependency chain to verify whether all required components actually exist in the loadout.

## How to Use

1. Identify the skill under audit
2. Extract `Composes:` / `Imports:` / `References:` fields
3. For each dependency, check whether the file exists at the claimed path
4. Render dependency graph with MISSING nodes flagged

## Key Insight

> A skill that COMPOSES other skills is only as valid as the weakest link in its dependency chain. The lens surfaces invisible assumptions.

## Output Format

```json
{
  "skill": "<target>",
  "dependencies": ["dep1", "dep2"],
  "missing": [],
  "verdict": "COMPOSITION_VALID" | "COMPOSITION_BROKEN"
}
```

## Rarity Justification

Single-skill analytical lens, not a composition itself — qualifies as uncommon.
