# Quality Gate Pipeline

## Type: recipe

## Rarity: uncommon

## Description

Composes a skill-quality check into a gate that fails fast on broken skills, passing verified ones downstream.

## Composition

```yaml
pipeline:
  - skill: chain_verifier_recipe
    purpose: verify composition chains are sound
  - skill: test_skill
    purpose: execute and validate skill behavior
```

## Invocation

```bash
# Run the quality gate on a target skill
SKILL_PATH="$1"  # e.g. crafted/my_skill.md

# Stage 1: verify composition
claude --print "$(cat chain_verifier_recipe.md)" --arg SKILL_PATH

# Stage 2: execute tests
claude --print "$(cat test_skill)" --arg SKILL_PATH

# Exit 0 only if both stages pass
```

## Exit Codes

- `0` — skill passes gate (verified + tested)
- `1` — composition failure
- `2` — test failure
- `3` — missing inputs

## Rarity Basis

Uses 2 loadout skills; idempotent; fits the gatekeeper role in any pipeline.
