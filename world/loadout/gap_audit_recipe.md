# Recipe: Gap Audit + Fill Pipeline

**Type:** Recipe
**Rarity:** Rare
**Composes:** loadout_reader + dependency_checker → Gap-Filled Loadout

## Purpose

Given the Stage 1 reframe ("Craft skills that address VERIFIED gaps in the loadout"), this recipe audits the loadout for missing skill dependencies, identifies what needs to be crafted, and produces a gap-filling plan.

## Ingredients

1. **loadout_reader** — Reads all skills in loadout/ directory
2. **dependency_checker** — Extracts and verifies declared dependencies

## Pipeline Steps

### Step 1: Scan Loadout

Read all `.md` files in loadout/. For each skill:
- Extract `**Type:**` field (Template/Lens/Recipe/etc.)
- Extract `## Composes:` or `Ingredients` section
- Extract `**Ingredients Required**` or similar dependency declarations

### Step 2: Build Dependency Graph

```
Loadout Skills:
├── inversion_second_order_recipe.md
│   ├── Dependency: constraint_inversion_lens (crafted/)
│   └── Dependency: second_order_lens (crafted/)
└── chain_verifier_recipe.md
    ├── Dependency: Divergence Lens (crafted/)
    └── Dependency: Convergence Lens (crafted/)

Available Files:
├── inversion_second_order_recipe.md ✓
├── chain_verifier_recipe.md ✓
└── reform_verify_pipeline.md ✓
```

### Step 3: Identify Gaps

For each declared dependency, check if the file exists in `crafted/` or `loadout/`.

**Current Gaps Found:**
- `crafted/constraint_inversion_lens.md` — MISSING (referenced by inversion_second_order_recipe)
- `crafted/second_order_lens.md` — MISSING (referenced by inversion_second_order_recipe)  
- `crafted/divergence_lens.md` — MISSING (referenced by chain_verifier_recipe)
- `crafted/convergence_lens.md` — MISSING (referenced by chain_verifier_recipe)

### Step 4: Gap Impact Analysis

| Missing Skill | Affected Recipe | Impact |
|--------------|-----------------|--------|
| constraint_inversion_lens | inversion_second_order_recipe | Cannot run Stage 1 |
| second_order_lens | inversion_second_order_recipe | Cannot run Stage 2 |
| divergence_lens | chain_verifier_recipe | Cannot run Divergence check |
| convergence_lens | chain_verifier_recipe | Cannot run Convergence check |

### Step 5: Gap-Fill Plan

**Priority 1 (Critical):**
1. Create `crafted/constraint_inversion_lens.md` — Core to inversion pipeline
2. Create `crafted/second_order_lens.md` — Core to inversion pipeline

**Priority 2 (High):**
3. Create `crafted/divergence_lens.md` — Core to verification
4. Create `crafted/convergence_lens.md` — Core to verification

## Output Schema

```json
{
  "loadout_size": <count>,
  "recipes_found": <count>,
  "lenses_found": <count>,
  "gaps_identified": <count>,
  "critical_gaps": ["<list of critical missing skills>"],
  "fill_plan": [{"skill": "<name>", "priority": "<1-3>", "reason": "<why needed>"}]
}
```

## Quality Gates

- [ ] At least 3 loadout skills scanned
- [ ] At least 2 gaps identified (otherwise loadout is complete)
- [ ] Fill plan includes priority ranking
- [ ] Each gap lists the affected recipe(s)

## Why This Improves the Repo

Without this recipe:
- Recipes reference missing dependencies
- Agents try to run compositions and fail
- Gate tests fail with cryptic errors

With this recipe:
- Gaps are identified BEFORE attempting composition
- Missing skills get crafted first
- Composition pipelines succeed more often
