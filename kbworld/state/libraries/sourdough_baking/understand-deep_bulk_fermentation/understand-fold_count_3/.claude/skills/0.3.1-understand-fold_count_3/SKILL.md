---
name: 0.3.1-understand-fold_count_3
description: [0.3.1] The complete ordered sequence of all stretch and fold repetitions scheduled for a single bulk fermentation, de
---

# understand-fold_count_3

**CALL NUMBER:** `deep_bulk_fermentation.fold_count_3 : sourdough_baking(5)`
**DEFINITION:** The complete ordered sequence of all stretch and fold repetitions scheduled for a single bulk fermentation, defined by fold_count total and fold_interval timing.

Invoke this skill to understand `fold_count_3` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_bulk_fermentation`
- **fold_count_2** (d1): The elapsed time interval between consecutive stretch and fold repetitions, typically 30 to 60 minutes, balancing dough development against excessive handling.
- **fold_count_8** (d1): The degree to which the number of folds produces visible and tactile improvements in dough_strength and gluten_development, measurable by dough extensibility and windowpane test.
- **fold_count_5** (d2): The temporal placement and scheduling of each fold within the broader bulk fermentation window, determining whether folds occur early middle or late in fermentation.

### from `sourdough_baking`
- **stretch_and_fold** (d1): Method of periodically stretching dough quarters and folding them into the center during bulk fermentation to develop structure without degassing.
- **gluten_development** (d2): Process of hydrating and aligning gluten proteins through mixing, folding, or autolyse to create strong extensible dough.
- **dough_consistency** (d2): Viscosity and handling quality from soft and extensible to firm and tight
- **bread_volume** (d3): Total size and height of finished loaf indicating proper fermentation and oven spring
- **crumb_structure** (d3): Internal architecture of bread defined by bubble size, distribution, and tenderness

## CONSUMERS (what needs this)
`fold_count_4`, `fold_count_6`

---
*Projected from the `sourdough baking` KB (517 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
