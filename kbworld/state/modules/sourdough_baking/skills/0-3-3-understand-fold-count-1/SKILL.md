---
name: 0.3.3-understand-fold_count_1
description: "[0.3.3] The specific iteration number assigned to each stretch and fold repetition within a bulk fermentation sequence"
---

# understand-fold_count_1

**CALL NUMBER:** `deep_bulk_fermentation.fold_count_1 : deep_fermentation(26), sourdough_baking(23), deep_lactobacillus(2)`
**DEFINITION:** The specific iteration number assigned to each stretch and fold repetition within a bulk fermentation sequence, typically numbered sequentially from 1 to total_folds.

Invoke this skill to understand `fold_count_1` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **flavor_complexity** (d4): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.
- **estolide_compounds** (d5): Aroma-active ester compounds produced by microbial esterification during fermentation, including banana, pineapple, floral, and fruity esters contributed by both lactobacillus and wild_yeast metabolism that layer upon organic_acid tanginess to create sourdough flavor_complexity.
- **lactobacillus_derived_estolides** (d5): Estolide_compounds synthesized by lactobacillus metabolism through esterification reactions between organic_acids and ethanol, contributing fruity, floral, and banana-like ester notes to sourdough flavor_complexity during fermentation.
- **yeast_derived_estolides** (d5): Estolide_compounds synthesized by wild_yeast metabolic activity, primarily through ethanol production that serves as the donor for esterification reactions with organic_acids, contributing to the fruity and floral ester layer of sourdough flavor_complexity.
- **crumb_porosity** (d6): The size, distribution, and uniformity of gas pockets in bread crumb created by carbon_dioxide expansion within the gluten network during fermentation, determining whether the crumb structure is open and honeycomb-like or tight and dense.
- **estolide_banana_compounds** (d6): Estolide_compounds with banana-like ester structures including isoamyl acetate and phenylethyl acetate that impart ripe banana and tropical fruit notes to sourdough flavor complexity.
- **estolide_floral_notes** (d6): Delicate floral aroma descriptors including rose, violet, and blossom derived from estolide_compounds such as phenylethyl acetate that contribute fragrant complexity to sourdough beyond the tanginess of organic_acids.
- **estolide_fruity_notes** (d6): Fruit-forward aroma contributions including tropical, stone fruit, and citrus descriptors from estolide_compounds produced during fermentation that create a layered flavor_complexity beyond organic_acid sourness in sourdough.
- **estolide_pineapple_compounds** (d6): Estolide_compounds with pineapple-like ester structures including ethyl butyrate and ethyl caproate that impart tropical fruit and pineapple notes to sourdough flavor complexity.
- **estolide_retention_in_crumb** (d6): The physical trapping and chemical binding of estolide_compounds within the gluten-starch matrix of bread crumb during baking, enabling their gradual volatilization during mastication to extend fruity and floral aftertaste perception.
- **estolide_role_in_aftertaste_curve** (d6): The contribution of estolide_compounds to the temporal progression of sourdough flavor perception after swallowing, where their slow volatilization from crumb_matrix_binding creates a lingering fruity and floral aftertaste that extends beyond organic_acid tanginess.
- **estolide_esterification_catalysis** (d6): The enzyme-mediated chemical reaction combining ethanol with organic_acids to form estolide_compounds as esters, catalyzed by microbial esterases during fermentation that enables the conversion of alcohol and acid precursors into fruity and floral aroma molecules.
- **estolide_acid_balance_dependency** (d6): The degree to which estolide_compounds interact with organic_acids such that their fruity and floral contributions are modulated by the lactic_acid to acetic_acid ratio, shifting flavor_complexity between creamy softness and sharp tanginess.
- **banneton_flouring** (d6): Dusting the interior of a proofing basket with flour before placing shaped dough, preventing sticking and creating decorative flour patterns on the finished crust.

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
- **acid_persistence_capacity** (d5): The ability of organic_acids to remain perceptibly present on the palate after swallowing, determined by acid molecular structure, concentration in crumb, and binding affinity to bread matrix components.
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
- **lingering_sensation_profile** (d5): The specific sequence and combination of taste impressions that unfold in the mouth after swallowing, including sour, bitter, sweet, and umami elements in their temporal order.
- **umami_afterglow** (d5): Savory, mouth-coating sensation that persists after swallowing, contributed by glutamate compounds from lactobacillus metabolism and nucleotide derivatives from wild_yeast activity.
- **sour_linger** (d5): Persistent sour taste sensation extending beyond initial swallowing, driven by acetic_acid and lactic_acid residues that remain on taste receptors due to their molecular persistence and crumb matrix release rate.
- **fermentation_vigor** (d5): Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.
- **temporal_aftertaste_curve** (d6): The time-based trajectory of aftertaste sensation intensity from moment of swallowing through gradual decay to baseline, characterized by rise, peak, plateau, and fade phases.
- **sweet_tail** (d6): Subtle perception of sweetness at the tail end of aftertaste, arising from residual maltose未被发酵and mmaltolytic_note generation during baking that lingers as palate sensation.
- **aftertaste_intensity** (d6): The perceptual strength of lingering sensations measured by how prominently organic_acids and aroma_compounds register on the palate after swallowing, ranging from subtle to pronounced.
- **bitter_finish** (d6): Astringent and slightly drying sensation that signals the end of the eating experience, influenced by phenolic compounds, over-fermented organic_acids, and Maillard reaction byproducts.
- **aroma_retention_capacity** (d6): The extent to which aroma_compounds become trapped within the bread crumb structure during baking and cooling, enabling continued volatilization in the mouth during and after swallowing.
- **finish_quality** (d6): The overall character and desirability of the final aftertaste impression, combining maltolytic_note finish, higher_alcohol contribution, and organic_acid linger into a coherent closing sensation.

### from `deep_lactobacillus`
- **estolide_contribution_to_complexity** (d6): The specific manner by which estolide_compounds enhance sourdough flavor complexity through fruity floral and tropical aroma contributions that layer upon organic_acid tanginess
- **estolide_impact_on_lingering_sensation** (d6): The way estolide compounds persist on palate receptors prolonging fruity floral aftertaste sensations beyond initial swallow

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
*Projected from the `sourdough baking` KB (546 concepts / 365 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
