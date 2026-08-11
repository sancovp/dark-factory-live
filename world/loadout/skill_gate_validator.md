# SKILL — skill_gate_validator (recipe)
ok
## Metadata
- **type**: recipe
- **composed_from**: [dependency_lens, gate_criteria_runner]
- **rarity**: uncommon
- **author**: agent_001

## What It Does

This recipe validates a skill before loadout admission by running two composed checks in sequence:

1. **dependency_lens** — verifies the skill's declared dependencies exist in the loadout directory. Fails fast if any hard dep is missing.

2. **gate_criteria_runner** — exercises the actual gate test for the skill type (lens → lens gate, recipe → pipeline test, tool → invocation test). Returns fitness 0 if composition fails end-to-end.

The pipeline short-circuits: if dependency_lens fails, gate_criteria_runner is never invoked.

## Composition

```yaml
pipeline:
  stages:
    - skill: dependency_lens
      inputs:
        skill_path: "${SKILL_PATH}"
      on_fail: abort
    - skill: gate_criteria_runner
      inputs:
        skill_path: "${SKILL_PATH}"
      on_fail: set_fitness_zero

env:
  SKILL_PATH: "<path to skill markdown file>"
```

## Pass Criteria

| Stage | Pass | Fail |
|-------|------|------|
| dependency_lens | → gate_criteria_runner | fitness=0, abort |
| gate_criteria_runner | fitness=1.0 | fitness=0 |

## Why This Matters

Per `dependency_proof_before_loadout` and `gate_listed_not_gate_passed`: a skill can exist in loadout but still revert at gate. This pipeline ensures both guarantees hold before declaring loadout-ready.

## Usage

```bash
# Validate a skill before listing/trading
SKILL_PATH=crafted/my_skill.md run skill_gate_validator
```

## Limitations

- Does not verify skill quality beyond gate criteria
- No recursion check (composed skills deps not deep-verified)
- Assumes dependency_lens and gate_criteria_runner are in loadout
