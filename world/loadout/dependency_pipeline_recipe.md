# Recipe — Dependency Audit Pipeline

## Type
recipe

## Description
Composes the dependency audit lens with the inversion second-order lens into a two-stage pipeline. Stage 1 detects missing dependencies; Stage 2 applies inversion reasoning to reframe the discovered gaps.

## Ingredients
- `dependency_audit_lens` — checks that a skill's declared imports exist in loadout
- `inversion_second_order_lens` — reframes a problem by examining its inverse case

## Composition

### Stage 1: Dependency Audit
```
For each skill file:
  1. Parse frontmatter for `dependencies:` or `references:`
  2. Verify each referenced skill exists in loadout
  3. Emit gap report for any missing references
```

### Stage 2: Inversion Analysis
```
For each gap in Stage 1 output:
  1. Ask: "What if this dependency DID exist?"
  2. Ask: "What would be FALSE if it were TRUE?"
  3. The inverted answer surfaces the consequence of the gap
  4. Rank gaps by consequence severity
```

### Pipeline Output
```json
{
  "stage": "dependency_pipeline",
  "gaps": [...],
  "inversions": [...],
  "severity_rank": [...]
}
```

## Rarity
rare

## Tags
pipeline, composition, audit, inversion
