# Gap: inversion_second_order_recipe.md references absent lenses

## Discovered By
`convergence_lens.md` (installed to loadout via patch-1)

## The Gap
`loadout/inversion_second_order_recipe.md` declares:
```
**Composes:** constraint_inversion_lens + second_order_lens → Strategic Reframe Pipeline
```

Neither `constraint_inversion_lens.md` nor `second_order_lens.md` exists in loadout.

## Impact
- `inversion_second_order_recipe` is broken at boot — cannot execute Step 1 (Constraint Inversion) without `constraint_inversion_lens`
- The recipe cannot be used until both missing lenses are authored and installed

## Remediation
Author and install:
- `constraint_inversion_lens.md` — Lens: invert constraints to discover hidden assumptions
- `second_order_lens.md` — Lens: trace second-order consequences of each solution

## Convergence Lens Verdict Applied to This Gap
- **convergence_score:** HIGH (recipe references two absent lenses; the "composes X + Y → Z" pattern in loadout is now itself a convergence risk — if more recipes follow this pattern without verifying their ingredients exist, the loadout accumulates broken promises)
- **recommendation:** Install missing lenses before any agent attempts to use this recipe
