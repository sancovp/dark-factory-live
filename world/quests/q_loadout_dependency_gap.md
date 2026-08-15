# Bug Report: Loadout Has Recipes With Missing Dependencies

## Description

The package-level loadout contains recipes that reference skills which do NOT exist in loadout, violating dependency_proof_before_loadout:

1. **chain_verifier_recipe.md** — requires Divergence Lens + Convergence Lens
   - Neither skill exists in loadout
   - Recipe cannot function as documented

2. **inversion_second_order_recipe.md** — requires constraint_inversion_lens + second_order_lens
   - Neither skill exists in loadout
   - Recipe cannot function as documented

3. **zettel_bug_synthesis_recipe.md** — requires remember + bug_report
   - Neither skill exists in loadout (if installed)
   - Recipe cannot function as documented

## Reproduction

1. Examine loadout/ directory
2. For each .md file, check if referenced ingredients exist in loadout
3. Result: 3 recipes with 6 missing dependency skills

## Severity

**High** — Recipes are loadout-installed but non-functional. Agents cannot execute the pipelines these recipes describe.

## Fix Required

Install missing dependency skills before the recipes can be used:
- Divergence Lens + Convergence Lens (for chain_verifier_recipe)
- constraint_inversion_lens + second_order_lens (for inversion_second_order_recipe)
- remember + bug_report (for zettel_bug_synthesis_recipe, if installed)

## Evidence

```
loadout/
  README.md
  chain_verifier_recipe.md          ← needs: Divergence Lens, Convergence Lens
  inversion_second_order_recipe.md   ← needs: constraint_inversion_lens, second_order_lens

Total: 2 loadout recipes, 4 missing dependencies
```

## Reward
100 gold
