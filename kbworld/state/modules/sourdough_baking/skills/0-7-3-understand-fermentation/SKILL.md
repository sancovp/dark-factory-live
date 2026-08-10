---
name: 0.7.3-understand-fermentation
description: "[0.7.3] Metabolic process where microbes convert sugars to CO2 for rise and acids for sour flavor"
---

# understand-fermentation

**CALL NUMBER:** `sourdough_baking.fermentation : deep_fermentation(34), deep_lactobacillus(4)`
**DEFINITION:** Metabolic process where microbes convert sugars to CO2 for rise and acids for sour flavor

Invoke this skill to understand `fermentation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **flavor_complexity** (d1): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.

### from `deep_fermentation`
- **fermentation_byproducts** (d1): Compounds produced by microbial fermentation including carbon dioxide for dough rise, lactic and acetic acids for sour flavor, and alcohols for aroma.
- **fc_acid_linger** (d2): The temporal persistence of organic acids on the palate after swallowing, determined by acid strength, concentration, and the buffering capacity of saliva, resulting in sour sensations that extend beyond the initial taste experience.
- **fc_sour_reverb** (d2): The echoing and reverberating quality of sour sensation in the aftertaste, where initial acid perception decays slowly and unevenly, creating wave-like sour peaks that persist after the main flavor has subsided.
- **carbon_dioxide** (d2): Gaseous byproduct of wild_yeast fermentation that provides dough rise and open crumb structure in sourdough bread.
- **estolide_moiety** (d2): A fatty acid ester linkage formed by condensation of a hydroxy fatty acid hydroxyl group with another fatty acid carboxyl group, creating a dimeric or oligomeric ester structure that serves as the foundational chemical scaffold for sourdough estolide compounds.
- **ethanol** (d2): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **organic_acids** (d2): Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine sourness_level and contribute to flavor_complexity.
- **aroma_compounds** (d2): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **fc_acid_balance_ratio** (d2): The proportional ratio between acetic_acid and lactic_acid concentrations that fundamentally determines whether the tanginess is sharp and vinegary or soft and creamy
- **fc_aftertaste_development** (d2): The evolving and lingering flavor sensations that persist after swallowing, shaped by organic_acid persistence and aroma_compound retention in the crumb
- **fc_estolide_compounds** (d2): Aroma-active ester compounds produced by yeast and lactobacillus that contribute fruity, floral, and sometimes banana or pineapple notes to sourdough flavor complexity
- **fc_fermentation_depth** (d2): The cumulative flavor intensity arising from extended fermentation periods allowing progressive accumulation of organic_acids and aroma_compounds in the dough matrix
- **fc_higher_alcohols** (d2): Complex alcohol byproducts of wild_yeast fermentation beyond ethanol that add nutty, floral, and rozaceous nuances to the overall flavor profile
- **fc_maltolytic_notes** (d2): Caramel, toasty, and biscuit-like flavor compounds derived from enzymatic breakdown of grain starches during fermentation and Maillard reactions during baking
- **fc_tanginess_profile** (d2): The specific character and quality of sour notes in sourdough ranging from sharp and pungent to mild and creamy, determined by the balance between acetic acid sharpness and lactic acid softness
- **fc_volatile_esters** (d2): Aroma compounds formed through esterification reactions between organic_acids and ethanol during fermentation, contributing fruity and floral notes
- **fc_yeast_character** (d2): The bready, nutty, sometimes fruity or floral flavor notes contributed by wild_yeast metabolic activity including higher alcohols and their derivatives during fermentation
- **fc_sweet_fade** (d2): Residual sweetness from grain-derived sugars and fermentation intermediates that slowly diminishes in the aftertaste, providing balance against sour and bitter notes and creating a pleasant conclusion to the flavor experience.
- **estolide_lactobacillus_contribution** (d2): The specific metabolic output of lactobacillus strains including enzyme secretion and substrate availability that drives estolide compound generation in sourdough fermentation.
- **estolide_yeast_contribution** (d2): The specific metabolic output of wild_yeast strains including esterase secretion and ethanol provision that participates in estolide compound formation and aroma profile development.
- **fc_aftertaste_evolution** (d2): The sequential unfolding and transformation of flavor notes during the aftertaste period, where initial sensations fade while secondary and tertiary flavor compounds reveal themselves progressively over time.
- **fc_mouthfeel_linger** (d2): Textural sensations including dryness, astringency, or creaminess that persist in the mouth after swallowing, contributing tactile dimensions to the aftertaste beyond pure taste perception.
- **fermentation_vigor** (d2): Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.
- **fc_crumb_aroma_trap** (d3): The mechanical retention of volatile aroma compounds within the porous crumb structure that slowly release during chewing and swallowing, contributing delayed and extended flavor contributions to the aftertaste.
- **fc_retro_nasal_release** (d3): The delayed release of volatile aroma compounds through the nasal passage during exhalation after swallowing, causing aftertaste flavors to emerge and evolve as trapped compounds in the crumb and oral cavity gradually vaporize.

### from `deep_lactobacillus`
- **elc_metabolite_pool** (d2): Organic acid and peptide metabolites secreted by lactobacillus that create the chemical environment favoring estolide stability.
- **elc_enzyme_secretion** (d2): Proteolytic and esterolytic enzymes released by lactobacillus strains into the sourdough matrix during fermentation.
- **elc_substrate_availability** (d2): The presence and accessibility of hydroxy fatty acid precursors and free fatty acids in the dough that lactobacillus metabolism can act upon.
- **hfap_fermentation_timing_factor** (d3): Temporal dimension of hydroxy fatty acid accumulation in sourdough, where extended fermentation allows progressive lipid oxidation and microbial hydroxylase activity to increase precursor availability for estolide_compounds synthesis.

### from `sourdough_baking`
- **acetic_acid** (d1): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d1): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **lactobacillus** (d1): Bacterial strains producing lactic and acetic acids that create sourdough tanginess
- **sourness_level** (d1): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced
- **wild_yeast** (d1): Naturally occurring yeast strains captured from flour and the environment that ferment dough, providing rise without commercial yeast.

## CONSUMERS (what needs this)
`bulk_fermentation`, `depleted_nutrients`, `pizza_dough`, `salt`, `sourdough_starter`

---
*Projected from the `sourdough baking` KB (510 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
