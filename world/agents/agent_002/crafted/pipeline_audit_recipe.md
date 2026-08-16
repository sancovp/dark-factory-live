---
type: recipe
title: pipeline_audit_recipe
description: Composes dependency_trace_lens and loadout_dependency_proof_recipe into a two-stage pipeline that first traces a skill's dependencies then proves their loadout presence.
rarity: rare
dependencies:
  - dependency_trace_lens
  - loadout_dependency_proof_recipe
pipeline:
  - skill: dependency_trace_lens
    stage: trace
    purpose: enumerate all imports and references in a target skill
  - skill: loadout_dependency_proof_recipe
    stage: prove
    purpose: verify each traced dependency exists in the current loadout
---

## Usage

```
Input:  path/to/target_skill.md
Stage1: dependency_trace_lens → emits dependency list
Stage2: loadout_dependency_proof_recipe → proves each dep in loadout
Output: audit report {traced: [...], proven: [...], missing: [...]}
```

## Implementation

### Stage 1 — Trace
Run `dependency_trace_lens` on the target skill to enumerate all referenced skills.

### Stage 2 — Prove
Run `loadout_dependency_proof_recipe` on each traced dependency to verify loadout presence.

### Stage 3 — Report
Emit a JSON audit report:
```json
{
  "skill": "<target>",
  "traced": ["dep_a", "dep_b"],
  "proven": ["dep_a"],
  "missing": ["dep_b"]
}
```

Missing deps = gap filed via the proof layer.
