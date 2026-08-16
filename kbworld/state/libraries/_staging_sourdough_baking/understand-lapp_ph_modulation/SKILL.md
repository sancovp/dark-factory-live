# understand-lapp_ph_modulation

**CALL NUMBER:** `deep_le_activity.lapp_ph_modulation : sourdough_baking(3), deep_fermentation(3), deep_lactobacillus(1)`
**DEFINITION:** The influence of dough pH on the ionization state of organic_acid substrates, affecting their availability as le_organic_acid_substrate and thus modulating lactobacillus_esterase_activity acyl donor preference.

Invoke this skill to understand `lapp_ph_modulation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **fd_acid_profile_evolution** (d2): The shifting ratio between lactic_acid and acetic_acid concentrations as fermentation_depth progresses, where early stages favor lactic_acid dominance and extended time increases acetic_acid proportion, sharpening the tanginess_profile toward vinegary character.
- **fd_sensory_threshold_crossing** (d3): The fermentation_depth milestone where organic_acid concentration crosses from subtle background tanginess into pronounced sourness_level that fundamentally defines the loaf character rather than merely complementing it.
- **fd_overfermentation_boundary** (d4): The fermentation_depth limit beyond which undesirable flavor characteristics emerge including pronounced banana_ester_notes, excessive acetic_acid sharpness, and structural collapse from overripe lactobacillus_esterase_activity and wild_yeast_esterase_activity dysregulation.

### from `deep_lactobacillus`
- **le_ph_effect** (d1): The influence of dough acidity on lactobacillus_esterase_activity, with optimal esterification catalysis occurring within specific pH ranges that preserve enzyme structure while maintaining substrate availability.

### from `sourdough_baking`
- **acetic_acid** (d1): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d1): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **sourness_level** (d2): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced

## CONSUMERS (what needs this)
`le_acyl_donor_preference`

---
*Projected from the `sourdough baking` KB (630 concepts / 458 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*