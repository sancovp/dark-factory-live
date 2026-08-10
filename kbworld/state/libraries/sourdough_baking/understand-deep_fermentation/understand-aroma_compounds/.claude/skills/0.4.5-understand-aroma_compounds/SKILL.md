---
name: 0.4.5-understand-aroma_compounds
description: [0.4.5] Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
---

# understand-aroma_compounds

**CALL NUMBER:** `deep_fermentation.aroma_compounds : deep_lactobacillus(1)`
**DEFINITION:** Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.

Invoke this skill to understand `aroma_compounds` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **fragrance_dwell** (d1): The lingering presence of fruity, floral, or ester-derived aroma notes in the aftertaste, attributed to fc_volatile_esters and fc_estolide_compounds with low volatility.
- **retronasal_aroma** (d1): Volatile aroma compounds released in the mouth after swallowing that travel to the olfactory receptors via the retronasal passage, forming a key component of sourdough aftertaste.
- **volatile_release_rate** (d1): The speed at which aroma_compounds evaporate and reach olfactory receptors in the mouth after swallowing, determining whether aftertaste aromatics are fleeting or prolonged.
- **aftertaste_intensity_decay** (d2): The rate at which perceived aftertaste strength diminishes over time, influenced by the molecular properties of organic_acids and aroma_compounds present.

### from `deep_lactobacillus`
- **lactate_estolide_volatility_profile** (d2): Evaporation rate and atmospheric persistence characteristics of lactate estolide aroma compounds determining whether buttery-creamy notes are fleeting or lingering

## CONSUMERS (what needs this)
`caramelized_aroma`, `esters`, `ethanol`, `flavor_complexity`, `fusel_alcohols`

---
*Projected from the `sourdough baking` KB (517 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
