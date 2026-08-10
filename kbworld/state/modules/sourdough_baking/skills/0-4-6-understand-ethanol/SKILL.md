---
name: 0.4.6-understand-ethanol
description: "[0.4.6] Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to "
---

# understand-ethanol

**CALL NUMBER:** `deep_fermentation.ethanol`
**DEFINITION:** Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.

Invoke this skill to understand `ethanol` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **aroma_compounds** (d1): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **estolide_yeast_contribution** (d1): The specific metabolic output of wild_yeast strains including esterase secretion and ethanol provision that participates in estolide compound formation and aroma profile development.
- **fc_retro_nasal_release** (d1): The delayed release of volatile aroma compounds through the nasal passage during exhalation after swallowing, causing aftertaste flavors to emerge and evolve as trapped compounds in the crumb and oral cavity gradually vaporize.
- **fc_crumb_aroma_trap** (d2): The mechanical retention of volatile aroma compounds within the porous crumb structure that slowly release during chewing and swallowing, contributing delayed and extended flavor contributions to the aftertaste.

## CONSUMERS (what needs this)
`fc_fermentation_depth`, `fermentation_byproducts`, `flavor_complexity`, `wild_yeast`

---
*Projected from the `sourdough baking` KB (510 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
