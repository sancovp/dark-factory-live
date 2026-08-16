---
name: 0.3.3-understand-fold_count_1
description: "[0.3.3] The specific iteration number assigned to each stretch and fold repetition within a bulk fermentation sequence"
---

# understand-fold_count_1

**CALL NUMBER:** `deep_bulk_fermentation.fold_count_1 : deep_fermentation(30), sourdough_baking(23), deep_lactobacillus(6)`
**DEFINITION:** The specific iteration number assigned to each stretch and fold repetition within a bulk fermentation sequence, typically numbered sequentially from 1 to total_folds.

Invoke this skill to understand `fold_count_1` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **flavor_complexity** (d4): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.
- **banneton_flouring** (d6): Dusting the interior of a proofing basket with flour before placing shaped dough, preventing sticking and creating decorative flour patterns on the finished crust.
- **fermentation_depth** (d7): The extent of sourdough fermentation progression, encompassing duration and metabolic development, where extended time enables enzymatic esterification between organic_acids and ethanol to produce fruity and floral aroma compounds.
- **fd_fermentation_vigor** (d7): Intensity and rate of the combined microbial fermentation process in sourdough driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.

### from `deep_bulk_fermentation`
- **fold_count_4** (d1): The predetermined total number of stretch and fold repetitions for a given recipe or bulk fermentation, the core metric that defines fold_count itself.
- **fold_count_10** (d2): Excessive number of folds causing dough exhaustion, overdevelopment, or tearing that degrades crumb_structure and flavor_complexity.
- **fold_count_3** (d2): The complete ordered sequence of all stretch and fold repetitions scheduled for a single bulk fermentation, defined by fold_count total and fold_interval timing.
- **fold_count_9** (d2): Insufficient number of folds resulting in weak gluten network, poor dough_consistency, and reduced bread_volume due to inadequate structural development.
- **fold_count_2** (d3): The elapsed time interval between consecutive stretch and fold repetitions, typically 30 to 60 minutes, balancing dough development against excessive handling.
- **fold_count_8** (d3): The degree to which the number of folds produces visible and tactile improvements in dough_strength and gluten_development, measurable by dough extensibility and windowpane test.
- **fold_count_5** (d4): The temporal placement and scheduling of each fold within the broader bulk fermentation window, determining whether folds occur early middle or late in fermentation.

### from `deep_fermentation`
- **fermentation_byproducts** (d4): Compounds produced by microbial fermentation including carbon dioxide for dough rise, lactic and acetic acids for sour flavor, and alcohols for aroma.
- **fd_acid_profile_evolution** (d5): The shifting ratio between lactic_acid and acetic_acid concentrations as fermentation_depth progresses, where early stages favor lactic_acid dominance and extended time increases acetic_acid proportion, sharpening the tanginess_profile toward vinegary character.
- **carbon_dioxide** (d5): Gaseous byproduct of wild_yeast fermentation that provides dough rise and open crumb structure in sourdough bread.
- **ethanol** (d5): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **organic_acids** (d5): Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine sourness_level and contribute to flavor_complexity.
- **aroma_compounds** (d5): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **fc_acid_balance_ratio** (d5): The proportional ratio between acetic_acid and lactic_acid concentrations that fundamentally determines whether the tanginess is sharp and vinegary or soft and creamy
- **fc_aftertaste_development** (d5): The evolving and lingering flavor sensations that persist after swallowing, shaped by organic_acid persistence and aroma_compound retention in the crumb
- **fc_estolide_compounds** (d5): Aroma-active ester compounds produced by yeast and lactobacillus that contribute fruity, floral, and sometimes banana or pineapple notes to sourdough flavor complexity
- **fc_fermentation_depth** (d5): The cumulative flavor intensity arising from extended fermentation periods allowing progressive accumulation of organic_acids and aroma_compounds in the dough matrix
- **fc_higher_alcohols** (d5): Complex alcohol byproducts of wild_yeast fermentation beyond ethanol that add nutty, floral, and rozaceous nuances to the overall flavor profile
- **fc_maltolytic_notes** (d5): Caramel, toasty, and biscuit-like flavor compounds derived from enzymatic breakdown of grain starches during fermentation and Maillard reactions during baking
- **fc_tanginess_profile** (d5): The specific character and quality of sour notes in sourdough ranging from sharp and pungent to mild and creamy, determined by the balance between acetic acid sharpness and lactic acid softness
- **fc_volatile_esters** (d5): Aroma compounds formed through esterification reactions between organic_acids and ethanol during fermentation, contributing fruity and floral notes
- **fc_yeast_character** (d5): The bready, nutty, sometimes fruity or floral flavor notes contributed by wild_yeast metabolic activity including higher alcohols and their derivatives during fermentation
- **fd_stage_active** (d5): The mid-fermentation phase where fermentation_vigor peaks, lactobacillus metabolism accelerates organic_acid production substantially, and aroma_compounds begin accumulating measurably in the dough matrix.
- **lactobacillus_esterase_activity** (d5): Enzymatic capability of lactobacillus strains to catalyze esterification reactions between organic_acids and ethanol during sourdough fermentation
- **fd_stage_initial** (d5): The early fermentation phase characterized by rapid wild_yeast carbon_dioxide production and nascent lactobacillus organic_acid generation, where flavor development remains minimal and the dough structure retains significant gluten integrity.
- **fermentation_vigor** (d5): Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.
- **wild_yeast_esterase_activity** (d5): Enzymatic contribution of wild_yeast strains to ester synthesis, primarily through ethanol production and potential direct ester formation pathways
- **fd_sensory_threshold_crossing** (d6): The fermentation_depth milestone where organic_acid concentration crosses from subtle background tanginess into pronounced sourness_level that fundamentally defines the loaf character rather than merely complementing it.
- **banana_ester_notes** (d6): Estolide_compounds (primarily isoamyl acetate) producing characteristic banana aroma contributions typical in overfermented sourdough
- **ester_contribution_to_flavor_complexity** (d6): The degree to which estolide_compounds enriches the overall sourdough flavor_complexity through combined fruity, floral, and tropical aroma notes
- **floral_ester_notes** (d6): Estolide_compounds creating rose, violet, and blossom aromatic impressions through lightweight volatile esters in the sourdough crumb
- **fruity_ester_notes** (d6): Estolide_compounds creating apple, pear, and tropical fruit aromatic impressions through specific ester structures in the sourdough headspace

### from `deep_lactobacillus`
- **banana_ester_threshold_concentration** (d7): The minimum isoamyl_acetate concentration required for human sensory perception of banana character. Exceeded in overfermented conditions where fermentation_vigor drives excessive ester accumulation beyond normal fruity_ester_notes levels.
- **banana_vs_fruity_ester_balance** (d7): The sensory distinction between isoamyl_acetate dominance (banana_ester_notes) versus broader fruity_ester_notes expression. At lower concentrations isoamyl acetate blends into general fruity complexity; at higher concentrations it distinctly reads as banana character.
- **fermentation_vigor_banana_interaction** (d7): The relationship between fermentation_vigor intensity and banana_ester_notes intensity. High fermentation_vigor accelerates both wild_yeast_esterase_activity and lactobacillus_esterase_activity, driving increased isoamyl_acetate production during vigorous overfermentation.
- **isoamyl_acetate** (d7): The primary ester compound (3-methylbutyl acetate) responsible for banana_ester_notes in sourdough. Formed through esterification between isoamyl alcohol (a higher_alcohol from wild_yeast fermentation) and acetic_acid during extended fermentation periods.
- **overfermentation_banana_association** (d7): The established correlation between extended fermentation timing and pronounced banana_ester_notes development. Extended fermentation_depth allows progressive accumulation of isoamyl_acetate beyond typical fruity_ester_notes concentrations, creating overripe banana rather than fresh fruit impressions.
- **isoamyl_alcohol** (d8): A branched-chain higher_alcohol byproduct of wild_yeast amino acid metabolism that serves as the alcohol substrate for isoamyl_acetate synthesis. Contributes nutty and fusel-like character alongside its ester derivatives.

### from `sourdough_baking`
- **bulk_fermentation** (d2): Primary fermentation phase where the mixed dough rests and ferments before shaping; time and temperature control gas production and flavor development.
- **dough_temperature** (d3): Target temperature of mixed dough (typically 75-80F/24-27C) ensuring predictable fermentation timing regardless of room conditions.
- **fermentation** (d3): Metabolic process where microbes convert sugars to CO2 for rise and acids for sour flavor
- **fermentation_temperature** (d3): Environmental temperature during bulk and final proof that directly controls fermentation speed; warmer accelerates, cooler slows.
- **fold_count** (d3): Number of stretch and fold repetitions during bulk fermentation for gluten development
- **proofing** (d3): Final fermentation phase where shaped dough rises before baking
- **stretch_and_fold** (d3): Method of periodically stretching dough quarters and folding them into the center during bulk fermentation to develop structure without degassing.
- **dough_consistency** (d3): Viscosity and handling quality from soft and extensible to firm and tight
- **overproofing** (d3): Excessive fermentation causing dough to collapse, lose structure, and create flat dense bread
- **acetic_acid** (d4): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d4): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **lactobacillus** (d4): Bacterial strains producing lactic and acetic acids that create sourdough tanginess
- **sourness_level** (d4): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced
- **wild_yeast** (d4): Naturally occurring yeast strains captured from flour and the environment that ferment dough, providing rise without commercial yeast.
- **banneton** (d4): Proofing basket made of woven rattan that supports shaped dough during final proof and leaves characteristic flour patterns on crust.
- **cold_retardation** (d4): Refrigerated proofing slowing fermentation for flavor development and scheduling flexibility
- **proofing_duration** (d4): Time allowance for final dough rise before scoring and baking
- **room_temperature_fermentation** (d4): Proofing at ambient warmth for faster fermentation with brighter flavors
- **underproofing** (d4): Insufficient fermentation leaving dough dense with tight crumb and raw starchy flavor
- **gluten_development** (d4): Process of hydrating and aligning gluten proteins through mixing, folding, or autolyse to create strong extensible dough.
- **bread_volume** (d4): Total size and height of finished loaf indicating proper fermentation and oven spring
- **crumb_structure** (d4): Internal architecture of bread defined by bubble size, distribution, and tenderness
- **rice_flour** (d5): Fine powder often used for dusting bannetons preventing sticking without dense crust

## CONSUMERS (what needs this)
`fold_count_7`

---
*Projected from the `sourdough baking` KB (630 concepts / 458 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
