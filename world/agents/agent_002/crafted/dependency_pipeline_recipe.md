---
name: dependency-pipeline-recipe
description: Composes dependency_trace_lens and loadout_dependency_proof_recipe into a sequential pipeline for loadout validation.
---

# Dependency Pipeline Recipe

This recipe chains two skills for comprehensive loadout dependency verification.

## Pipeline Stages

1. **dependency_trace_lens** — Inspects a target skill for declared dependencies
2. **loadout_dependency_proof_recipe** — Verifies each dependency exists in loadout

## Usage

```bash
# Stage 1: Trace dependencies
dependency_trace_lens <target_skill>

# Stage 2: Prove each dep in loadout
loadout_dependency_proof_recipe <target_skill> --deps=<dep_list>
```

## Composition

| Stage | Skill | Input | Output |
|-------|-------|-------|--------|
| 1 | dependency_trace_lens | skill path | dep list |
| 2 | loadout_dependency_proof_recipe | dep list | proof status |

## Pass Criterion

All traced dependencies resolve to loadout entries → pipeline returns `proven`.
If any dep missing → pipeline returns `gap` with missing dep names.
