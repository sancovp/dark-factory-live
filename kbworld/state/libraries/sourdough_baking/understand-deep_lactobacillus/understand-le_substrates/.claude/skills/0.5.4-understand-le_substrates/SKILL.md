---
name: 0.5.4-understand-le_substrates
description: [0.5.4] The molecular reactants consumed during lactobacillus_esterase_activity: organic_acids and ethanol that underg
---

# understand-le_substrates

**CALL NUMBER:** `deep_lactobacillus.le_substrates : sourdough_baking(3), deep_fermentation(2)`
**DEFINITION:** The molecular reactants consumed during lactobacillus_esterase_activity: organic_acids and ethanol that undergo esterification catalysis.

Invoke this skill to understand `le_substrates` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **ethanol** (d2): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **aroma_compounds** (d3): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.

### from `deep_lactobacillus`
- **le_ethanol_substrate** (d1): Alcohol produced by wild_yeast fermentation that serves as the nucleophile/acyl acceptor in esterification reactions catalyzed by lactobacillus_esterase_activity.
- **le_organic_acid_substrate** (d1): Carbon-chain acid substrates (lactic_acid and acetic_acid) from lactobacillus metabolism that serve as acyl donors in esterification reactions catalyzed by lactobacillus_esterase_activity.

### from `sourdough_baking`
- **acetic_acid** (d2): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d2): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **sourness_level** (d3): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced

## CONSUMERS (what needs this)
`le_activity`

---
*Projected from the `sourdough baking` KB (546 concepts / 369 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
