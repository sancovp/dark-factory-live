---
name: 0.4.2-understand-organic_acids
description: "[0.4.2] Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine s"
---

# understand-organic_acids

**CALL NUMBER:** `deep_fermentation.organic_acids : sourdough_baking(5), deep_lactobacillus(4)`
**DEFINITION:** Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine sourness_level and contribute to flavor_complexity.

Invoke this skill to understand `organic_acids` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **flavor_complexity** (d1): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.

### from `deep_fermentation`
- **estolide_hydroxy_fatty_acid_precursor** (d1): A hydroxy-bearing fatty acid substrate derived from grain lipid oxidation or microbial metabolism that provides the esterification site for estolide formation during sourdough fermentation.
- **fc_acid_linger** (d1): The temporal persistence of organic acids on the palate after swallowing, determined by acid strength, concentration, and the buffering capacity of saliva, resulting in sour sensations that extend beyond the initial taste experience.
- **fc_sour_reverb** (d1): The echoing and reverberating quality of sour sensation in the aftertaste, where initial acid perception decays slowly and unevenly, creating wave-like sour peaks that persist after the main flavor has subsided.
- **estolide_flavor_complexity_integration** (d2): The contribution of estolide compounds to the overall depth and nuance of sourdough taste through their role as aroma-active esters that layer fruity and floral notes atop the organic_acid sourness profile.
- **aroma_compounds** (d2): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **ethanol** (d2): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **fc_acid_balance_ratio** (d2): The proportional ratio between acetic_acid and lactic_acid concentrations that fundamentally determines whether the tanginess is sharp and vinegary or soft and creamy
- **fc_aftertaste_development** (d2): The evolving and lingering flavor sensations that persist after swallowing, shaped by organic_acid persistence and aroma_compound retention in the crumb
- **fc_estolide_compounds** (d2): Aroma-active ester compounds produced by yeast and lactobacillus that contribute fruity, floral, and sometimes banana or pineapple notes to sourdough flavor complexity
- **fc_fermentation_depth** (d2): The cumulative flavor intensity arising from extended fermentation periods allowing progressive accumulation of organic_acids and aroma_compounds in the dough matrix
- **fc_higher_alcohols** (d2): Complex alcohol byproducts of wild_yeast fermentation beyond ethanol that add nutty, floral, and rozaceous nuances to the overall flavor profile
- **fc_maltolytic_notes** (d2): Caramel, toasty, and biscuit-like flavor compounds derived from enzymatic breakdown of grain starches during fermentation and Maillard reactions during baking
- **fc_tanginess_profile** (d2): The specific character and quality of sour notes in sourdough ranging from sharp and pungent to mild and creamy, determined by the balance between acetic acid sharpness and lactic acid softness
- **fc_volatile_esters** (d2): Aroma compounds formed through esterification reactions between organic_acids and ethanol during fermentation, contributing fruity and floral notes
- **fc_yeast_character** (d2): The bready, nutty, sometimes fruity or floral flavor notes contributed by wild_yeast metabolic activity including higher alcohols and their derivatives during fermentation
- **fc_crumb_aroma_trap** (d3): The mechanical retention of volatile aroma compounds within the porous crumb structure that slowly release during chewing and swallowing, contributing delayed and extended flavor contributions to the aftertaste.
- **fc_retro_nasal_release** (d3): The delayed release of volatile aroma compounds through the nasal passage during exhalation after swallowing, causing aftertaste flavors to emerge and evolve as trapped compounds in the crumb and oral cavity gradually vaporize.
- **estolide_yeast_contribution** (d3): The specific metabolic output of wild_yeast strains including esterase secretion and ethanol provision that participates in estolide compound formation and aroma profile development.
- **fc_aftertaste_clarity** (d3): The definition and distinguishability of individual flavor notes within the lingering aftertaste, ranging from clear and articulated to muddled and indistinct, influenced by the complexity and balance of residual compounds.
- **fc_aftertaste_evolution** (d3): The sequential unfolding and transformation of flavor notes during the aftertaste period, where initial sensations fade while secondary and tertiary flavor compounds reveal themselves progressively over time.
- **fc_aftertaste_persistence** (d3): The duration and temporal extent of lingering flavor sensations after swallowing, measured by how long taste receptors remain activated by residual compounds in the mouth and retro-nasal space.
- **fc_bitterness_tail** (d3): Bitter flavor compounds from grain polyphenols and fermentation byproducts that emerge and linger at the end of the flavor sequence, providing a clean finish or an undesirable harsh tail depending on concentration and balance.
- **fc_mouthfeel_linger** (d3): Textural sensations including dryness, astringency, or creaminess that persist in the mouth after swallowing, contributing tactile dimensions to the aftertaste beyond pure taste perception.
- **fc_palate_coating** (d3): The physical film left on oral tissues by fermentation byproducts and organic acids that prolongs taste receptor exposure, creating sensations of mouthfeel that extend the aftertaste beyond flavor into tactile territory.
- **fc_salt_reverberation** (d3): Mineral notes from fermentation water and dissolved grain compounds that subtly persist through the aftertaste, enhancing flavor perception and contributing to the savory umami dimension of the lingering taste.

### from `deep_lactobacillus`
- **elc_metabolite_pool** (d1): Organic acid and peptide metabolites secreted by lactobacillus that create the chemical environment favoring estolide stability.
- **hfap_fermentation_timing_factor** (d1): Temporal dimension of hydroxy fatty acid accumulation in sourdough, where extended fermentation allows progressive lipid oxidation and microbial hydroxylase activity to increase precursor availability for estolide_compounds synthesis.
- **elc_enzyme_secretion** (d4): Proteolytic and esterolytic enzymes released by lactobacillus strains into the sourdough matrix during fermentation.
- **elc_substrate_availability** (d4): The presence and accessibility of hydroxy fatty acid precursors and free fatty acids in the dough that lactobacillus metabolism can act upon.

### from `sourdough_baking`
- **sourness_level** (d1): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced
- **acetic_acid** (d3): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d3): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **lactobacillus** (d3): Bacterial strains producing lactic and acetic acids that create sourdough tanginess
- **wild_yeast** (d3): Naturally occurring yeast strains captured from flour and the environment that ferment dough, providing rise without commercial yeast.

## CONSUMERS (what needs this)
`acid_generation_rate`, `fc_aftertaste_development`, `fc_fermentation_depth`, `fermentation_byproducts`, `fermentation_vigor`, `flavor_complexity`, `lactobacillus`

---
*Projected from the `sourdough baking` KB (510 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
