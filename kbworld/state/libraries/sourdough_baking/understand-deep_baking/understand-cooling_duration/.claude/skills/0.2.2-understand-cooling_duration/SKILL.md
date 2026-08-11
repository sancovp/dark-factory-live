---
name: 0.2.2-understand-cooling_duration
description: [0.2.2] Post-bake resting period of 1-2 hours where internal temperature stabilizes and crumb texture sets before slic
---

# understand-cooling_duration

**CALL NUMBER:** `deep_baking.cooling_duration : sourdough_baking(6)`
**DEFINITION:** Post-bake resting period of 1-2 hours where internal temperature stabilizes and crumb texture sets before slicing

Invoke this skill to understand `cooling_duration` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `sourdough_baking`
- **cooling** (d1): Post-bake rest allowing crumb structure to set and internal moisture to redistribute
- **crumb_doneness** (d2): Visual and tactile check confirming fully baked interior without raw dough
- **crumb_structure** (d2): Internal architecture of bread defined by bubble size, distribution, and tenderness
- **slicing** (d2): Cutting bread into portions after cooling for serving and storage
- **internal_temperature** (d3): Bread center temperature (typically 195-210F/90-99C) indicating doneness; lower temps leave gummy crumb.
- **bread_storage** (d3): Methods for maintaining bread freshness including paper bag (short term), plastic bag (longer), freezer (extended), or bread box.

## CONSUMERS (what needs this)
`cool`

---
*Projected from the `sourdough baking` KB (546 concepts / 365 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
