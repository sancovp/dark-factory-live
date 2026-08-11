# understand-fermentation

**CALL NUMBER:** `sourdough_baking.fermentation : deep_fermentation(22), deep_lactobacillus(6)`
**DEFINITION:** Metabolic process where microbes convert sugars to CO2 for rise and acids for sour flavor

Invoke this skill to understand `fermentation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **flavor_complexity** (d1): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.
- **fermentation_depth** (d4): The extent of sourdough fermentation progression, encompassing duration and metabolic development, where extended time enables enzymatic esterification between organic_acids and ethanol to produce fruity and floral aroma compounds.

### from `deep_fermentation`
- **fermentation_byproducts** (d1): Compounds produced by microbial fermentation including carbon dioxide for dough rise, lactic and acetic acids for sour flavor, and alcohols for aroma.
- **carbon_dioxide** (d2): Gaseous byproduct of wild_yeast fermentation that provides dough rise and open crumb structure in sourdough bread.
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
- **lactobacillus_esterase_activity** (d2): Enzymatic capability of lactobacillus strains to catalyze esterification reactions between organic_acids and ethanol during sourdough fermentation
- **fermentation_vigor** (d2): Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.
- **wild_yeast_esterase_activity** (d2): Enzymatic contribution of wild_yeast strains to ester synthesis, primarily through ethanol production and potential direct ester formation pathways
- **banana_ester_notes** (d3): Estolide_compounds (primarily isoamyl acetate) producing characteristic banana aroma contributions typical in overfermented sourdough
- **ester_contribution_to_flavor_complexity** (d3): The degree to which estolide_compounds enriches the overall sourdough flavor_complexity through combined fruity, floral, and tropical aroma notes
- **floral_ester_notes** (d3): Estolide_compounds creating rose, violet, and blossom aromatic impressions through lightweight volatile esters in the sourdough crumb
- **fruity_ester_notes** (d3): Estolide_compounds creating apple, pear, and tropical fruit aromatic impressions through specific ester structures in the sourdough headspace
- **pineapple_ester_notes** (d3): Estolide_compounds (primarily ethyl butyrate) producing pineapple-like ester notes in sourdough with high fermentation_vigor

### from `deep_lactobacillus`
- **banana_ester_threshold_concentration** (d4): The minimum isoamyl_acetate concentration required for human sensory perception of banana character. Exceeded in overfermented conditions where fermentation_vigor drives excessive ester accumulation beyond normal fruity_ester_notes levels.
- **banana_vs_fruity_ester_balance** (d4): The sensory distinction between isoamyl_acetate dominance (banana_ester_notes) versus broader fruity_ester_notes expression. At lower concentrations isoamyl acetate blends into general fruity complexity; at higher concentrations it distinctly reads as banana character.
- **fermentation_vigor_banana_interaction** (d4): The relationship between fermentation_vigor intensity and banana_ester_notes intensity. High fermentation_vigor accelerates both wild_yeast_esterase_activity and lactobacillus_esterase_activity, driving increased isoamyl_acetate production during vigorous overfermentation.
- **isoamyl_acetate** (d4): The primary ester compound (3-methylbutyl acetate) responsible for banana_ester_notes in sourdough. Formed through esterification between isoamyl alcohol (a higher_alcohol from wild_yeast fermentation) and acetic_acid during extended fermentation periods.
- **overfermentation_banana_association** (d4): The established correlation between extended fermentation timing and pronounced banana_ester_notes development. Extended fermentation_depth allows progressive accumulation of isoamyl_acetate beyond typical fruity_ester_notes concentrations, creating overripe banana rather than fresh fruit impressions.
- **isoamyl_alcohol** (d5): A branched-chain higher_alcohol byproduct of wild_yeast amino acid metabolism that serves as the alcohol substrate for isoamyl_acetate synthesis. Contributes nutty and fusel-like character alongside its ester derivatives.

### from `sourdough_baking`
- **acetic_acid** (d1): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d1): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **lactobacillus** (d1): Bacterial strains producing lactic and acetic acids that create sourdough tanginess
- **sourness_level** (d1): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced
- **wild_yeast** (d1): Naturally occurring yeast strains captured from flour and the environment that ferment dough, providing rise without commercial yeast.

## CONSUMERS (what needs this)
`bulk_fermentation`, `depleted_nutrients`, `pizza_dough`, `salt`, `sourdough_starter`

---
*Projected from the `sourdough baking` KB (546 concepts / 369 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*