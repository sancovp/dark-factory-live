---
name: 0.1.1-understand-flavor_complexity
description: "[0.1.1] The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced dur"
---

# understand-flavor_complexity

**CALL NUMBER:** `?.flavor_complexity : deep_fermentation(14), sourdough_baking(5)`
**DEFINITION:** The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.

Invoke this skill to understand `flavor_complexity` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **aroma_compounds** (d1): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **ethanol** (d1): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **fc_acid_balance_ratio** (d1): The proportional ratio between acetic_acid and lactic_acid concentrations that fundamentally determines whether the tanginess is sharp and vinegary or soft and creamy
- **fc_aftertaste_development** (d1): The evolving and lingering flavor sensations that persist after swallowing, shaped by organic_acid persistence and aroma_compound retention in the crumb
- **fc_estolide_compounds** (d1): Aroma-active ester compounds produced by yeast and lactobacillus that contribute fruity, floral, and sometimes banana or pineapple notes to sourdough flavor complexity
- **fc_fermentation_depth** (d1): The cumulative flavor intensity arising from extended fermentation periods allowing progressive accumulation of organic_acids and aroma_compounds in the dough matrix
- **fc_higher_alcohols** (d1): Complex alcohol byproducts of wild_yeast fermentation beyond ethanol that add nutty, floral, and rozaceous nuances to the overall flavor profile
- **fc_maltolytic_notes** (d1): Caramel, toasty, and biscuit-like flavor compounds derived from enzymatic breakdown of grain starches during fermentation and Maillard reactions during baking
- **fc_tanginess_profile** (d1): The specific character and quality of sour notes in sourdough ranging from sharp and pungent to mild and creamy, determined by the balance between acetic acid sharpness and lactic acid softness
- **fc_volatile_esters** (d1): Aroma compounds formed through esterification reactions between organic_acids and ethanol during fermentation, contributing fruity and floral notes
- **fc_yeast_character** (d1): The bready, nutty, sometimes fruity or floral flavor notes contributed by wild_yeast metabolic activity including higher alcohols and their derivatives during fermentation
- **organic_acids** (d1): Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine sourness_level and contribute to flavor_complexity.
- **carbon_dioxide** (d3): Gaseous byproduct of wild_yeast fermentation that provides dough rise and open crumb structure in sourdough bread.
- **fermentation_vigor** (d3): Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.

### from `sourdough_baking`
- **acetic_acid** (d2): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d2): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **lactobacillus** (d2): Bacterial strains producing lactic and acetic acids that create sourdough tanginess
- **wild_yeast** (d2): Naturally occurring yeast strains captured from flour and the environment that ferment dough, providing rise without commercial yeast.
- **sourness_level** (d2): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced

## CONSUMERS (what needs this)
`cold_retardation`, `fermentation`, `organic_acids`

---
*Projected from the `sourdough baking` KB (465 concepts / 268 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
