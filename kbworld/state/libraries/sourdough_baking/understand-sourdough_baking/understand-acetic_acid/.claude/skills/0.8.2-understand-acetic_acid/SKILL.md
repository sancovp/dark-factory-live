---
name: 0.8.2-understand-acetic_acid
description: [0.8.2] Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
---

# understand-acetic_acid

**CALL NUMBER:** `sourdough_baking.acetic_acid : deep_fermentation(3)`
**DEFINITION:** Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor

Invoke this skill to understand `acetic_acid` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **fd_acid_profile_evolution** (d1): The shifting ratio between lactic_acid and acetic_acid concentrations as fermentation_depth progresses, where early stages favor lactic_acid dominance and extended time increases acetic_acid proportion, sharpening the tanginess_profile toward vinegary character.
- **fd_sensory_threshold_crossing** (d2): The fermentation_depth milestone where organic_acid concentration crosses from subtle background tanginess into pronounced sourness_level that fundamentally defines the loaf character rather than merely complementing it.
- **fd_overfermentation_boundary** (d3): The fermentation_depth limit beyond which undesirable flavor characteristics emerge including pronounced banana_ester_notes, excessive acetic_acid sharpness, and structural collapse from overripe lactobacillus_esterase_activity and wild_yeast_esterase_activity dysregulation.

### from `sourdough_baking`
- **sourness_level** (d1): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced

## CONSUMERS (what needs this)
`acetic_acid_esterification`, `as_acetic_acid_ratio`, `as_sourness_level`, `fc_acid_balance_ratio`, `fermentation`, `fermentation_byproducts`, `isoamyl_acetate`, `lactobacillus`, `lactobacillus_esterase_activity`, `lapp_ph_modulation`, `le_organic_acid_substrate`

---
*Projected from the `sourdough baking` KB (630 concepts / 458 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
