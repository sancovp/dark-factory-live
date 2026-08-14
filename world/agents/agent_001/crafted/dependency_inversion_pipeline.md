# Dependency-Inversion Pipeline Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** `dependency_lens` + `inversion_second_order_recipe` → Dependency Failure Propagation Verifier

## The Problem

`dependency_lens` tells you WHAT is missing from a loadout. `inversion_second_order_recipe` tells you what happens after you act on a problem. Chained together, they answer a deeper question: if a dependency goes missing, what cascades — and which downstream skills in the pipeline break first?

Neither lens alone reveals the full chain of consequences. This recipe closes that gap.

## Ingredients Required

1. **`dependency_lens`** — Identify loadout gaps: what skills/components does the target skill require that are absent?
2. **`inversion_second_order_recipe`** — Trace the consequences of each identified gap once the composition runs

## Pipeline Stages

### Stage 1: Dependency Extraction (via dependency_lens)

For a given target skill:
1. Parse the skill file for import/reference statements
2. Check each referenced component against the live loadout directory
3. Flag every missing dependency as a **loadout gap**

**Output:** `Dependency_Report = {skill, missing_deps: [dep1, dep2, ...], safe_for_loadout: bool}`

### Stage 2: Second-Order Inversion (via inversion_second_order_recipe)

For each **loadout gap** from Stage 1:
1. Invert the gap: what if the dependency EXISTED when it shouldn't? What constraint would it violate?
2. Apply second-order tracing: who benefits if the gap is silently ignored? Who loses? What new failure modes emerge?
3. Identify the **propagation path**: how does this gap cascade through the chain

**Output:** `Second_Order_Report = {gap, propagation_path: [...], second_order_failures: [...], confidence: high/medium/low}`

### Stage 3: Pipeline Synthesis

```json
{
  "target_skill": "<path>",
  "stage1_gaps": [{"dep": "...", "status": "MISSING", "severity": "high/med/low"}],
  "stage2_propagation": [{"gap": "...", "propagation_path": [...], "second_order_failures": [...] }],
  "critical_gaps": ["dep1"],
  "pipeline_integrity": "SAFE / DEGRADED / BROKEN",
  "fix_recommendation": "install <dep> before running this pipeline"
}
```

## Quality Gates

- [ ] Stage 1 finds at least 1 dependency reference
- [ ] Stage 2 traces consequences for every identified gap
- [ ] At least one `second_order_failure` named per gap
- [ ] `pipeline_integrity` is SAFE / DEGRADED / BROKEN (not UNKNOWN)

## Why Epic

Chains a loadout-gap finder with a second-order failure tracer. Reveals failure cascades that static analysis alone misses. Directly addresses `dependency_proof_before_loadout` by making propagation risk explicit before installation.
