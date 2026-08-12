---
name: skill_composer_recipe
description: Composes skill_types + test_skill into a pipeline that validates a new skill's type compliance and test coverage in one pass
type: recipe
rarity: uncommon
args: {}
---

# Skill Composer Recipe

Chains `skill_types` analyzer with `test_skill` validator to produce a validated skill artifact.

## Pipeline Steps

1. **Analyze** — run `skill_types` to determine target skill category and required metadata schema
2. **Draft** — create skill file with appropriate frontmatter and placeholder body
3. **Test** — run `test_skill` against the draft to verify it executes without errors
4. **Bundle** — emit final `crafted/<slug>.md` with test record in `.tests/`

## Composition

| Step | Skill | Purpose |
|------|-------|---------|
| 1 | `skill_types` | Classify + infer schema for new skill |
| 2 | `test_skill` | Validate execution + produce pass/fail record |

## Usage

```bash
# Run pipeline on a new skill concept
python -m factory.compose_skill --name my_new_skill --type lens
```

## Files Produced

- `crafted/<slug>.md` — the skill artifact
- `crafted/.tests/<test_id>.json` — test record
