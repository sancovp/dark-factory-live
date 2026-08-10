# understand-fermentation_vigor

**CALL NUMBER:** `deep_fermentation.fermentation_vigor : deep_lactobacillus(20), sourdough_baking(5)`
**DEFINITION:** Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.

Invoke this skill to understand `fermentation_vigor` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **flavor_complexity** (d2): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.

### from `deep_fermentation`
- **carbon_dioxide** (d1): Gaseous byproduct of wild_yeast fermentation that provides dough rise and open crumb structure in sourdough bread.
- **organic_acids** (d1): Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine sourness_level and contribute to flavor_complexity.
- **acid_retention_capacity** (d2): The ability of the crumb matrix to retain organic_acids such that they continue to stimulate taste receptors after the bread is consumed, influenced by crumb porosity and acid binding.
- **aftertaste_tang_profile** (d2): The specific character of sour aftertaste sensations ranging from sharp and punchy to soft and creamy, shaped by the fc_acid_balance_ratio of persistent organic_acids.
- **bitterness_trail** (d2): Any lingering bitter notes in the aftertaste, often associated with certain organic_acids or fermentation byproducts that persist due to their solubility characteristics.
- **fce_esterification_pathway** (d2): Biochemical condensation reaction between organic_acids and ethanol catalyzed by microbial esterase and acyltransferase enzymes during sourdough fermentation.
- **tanginess_linger** (d2): The duration and intensity of sour taste sensations that persist in the mouth after swallowing, determined by organic_acid type and concentration.
- **aftertaste_duration** (d3): The total time elapsed from swallowing to the complete disappearance of sourdough flavor perception, determined by the slowest-clearing compounds in the aftertaste.
- **aroma_compounds** (d3): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **ethanol** (d3): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **fc_acid_balance_ratio** (d3): The proportional ratio between acetic_acid and lactic_acid concentrations that fundamentally determines whether the tanginess is sharp and vinegary or soft and creamy
- **fc_aftertaste_development** (d3): The evolving and lingering flavor sensations that persist after swallowing, shaped by organic_acid persistence and aroma_compound retention in the crumb
- **fc_estolide_compounds** (d3): Aroma-active ester compounds produced by yeast and lactobacillus that contribute fruity, floral, and sometimes banana or pineapple notes to sourdough flavor complexity
- **fc_fermentation_depth** (d3): The cumulative flavor intensity arising from extended fermentation periods allowing progressive accumulation of organic_acids and aroma_compounds in the dough matrix
- **fc_higher_alcohols** (d3): Complex alcohol byproducts of wild_yeast fermentation beyond ethanol that add nutty, floral, and rozaceous nuances to the overall flavor profile
- **fc_maltolytic_notes** (d3): Caramel, toasty, and biscuit-like flavor compounds derived from enzymatic breakdown of grain starches during fermentation and Maillard reactions during baking
- **fc_tanginess_profile** (d3): The specific character and quality of sour notes in sourdough ranging from sharp and pungent to mild and creamy, determined by the balance between acetic acid sharpness and lactic acid softness
- **fc_volatile_esters** (d3): Aroma compounds formed through esterification reactions between organic_acids and ethanol during fermentation, contributing fruity and floral notes
- **fc_yeast_character** (d3): The bready, nutty, sometimes fruity or floral flavor notes contributed by wild_yeast metabolic activity including higher alcohols and their derivatives during fermentation
- **fragrance_dwell** (d4): The lingering presence of fruity, floral, or ester-derived aroma notes in the aftertaste, attributed to fc_volatile_esters and fc_estolide_compounds with low volatility.
- **retronasal_aroma** (d4): Volatile aroma compounds released in the mouth after swallowing that travel to the olfactory receptors via the retronasal passage, forming a key component of sourdough aftertaste.
- **volatile_release_rate** (d4): The speed at which aroma_compounds evaporate and reach olfactory receptors in the mouth after swallowing, determining whether aftertaste aromatics are fleeting or prolonged.
- **aftertaste_sensory_profile** (d4): The composite quality of lingering flavor sensations after swallowing sourdough, encompassing taste, aroma, and mouthfeel dimensions that evolve over time.
- **fce_microbial_source_spectrum** (d4): The range of estolide-producing organisms spanning wild_yeast esterases and lactobacillus acyl-CoA transferases each yielding distinct estolide profiles.
- **fce_odor_threshold** (d4): Concentration at which specific estolide compounds become detectable by human olfaction, varying widely by estolide structure and carbon chain length.

### from `deep_lactobacillus`
- **umami_savory_character** (d2): The specific quality of savory, broth-like, meaty, or full-bodied taste notes in sourdough arising from glutamate concentration and nucleotide synergy, distinct from sweet, sour, salty, and bitter dimensions.
- **umami_aftertaste_duration** (d3): The temporal persistence of savory taste sensation after swallowing sourdough, determined by retention of free amino acids and peptides in the crumb matrix and their continued release during oral clearance.
- **lactate_estolide_formation_pathway** (d4): Biochemical condensation pathway where lactobacillus lactic_acid reacts with ethanol via acyl-CoA transferase enzymes to form lactate estolide linkages
- **lactate_estolide_volatility_profile** (d5): Evaporation rate and atmospheric persistence characteristics of lactate estolide aroma compounds determining whether buttery-creamy notes are fleeting or lingering
- **lactic_acid_esterification_mechanism** (d5): Specific biochemical reaction mechanism by which lactic_acid carboxylic group bonds with ethanol hydroxyl group forming ester bonds characteristic of lactate estolides
- **umami_microbial_protease_contribution** (d5): Proteolytic enzymes secreted by lactobacillus strains including aminopeptidases and endopeptidases that hydrolyze flour proteins into free amino acids contributing to umami sensation.
- **lactate_estolide_sensory_profile** (d5): Composite sensory character of lactate estolides encompassing buttery_note_contribution creamy_note_contribution and mild_fruity_note_contribution defining their distinct flavor identity
- **lactate_estolide_odor_threshold** (d5): Concentration at which specific lactate estolide compounds become detectable by human olfaction varying by carbon chain length and esterification degree
- **sharpness_comparison_to_acetate** (d5): Relative sensory differentiation where lactate estolides produce softer rounded tang versus acetate estolides producing sharper punchier notes
- **lactate_estolide_carbon_chain_variants** (d6): Structural variations in lactate estolides defined by carbon chain length of the lactic_acid moiety determining aroma intensity and character
- **buttery_note_contribution** (d6): Sensory attribute contributed by lactate estolides producing rich buttercream flavor impressions distinct from dairy-free sharp acetate estolides
- **creamy_note_contribution** (d6): Sensory attribute contributed by lactate estolides producing smooth mouthfeel impressions and lactone-like creamy flavor sensations
- **mild_fruity_note_contribution** (d6): Sensory attribute contributed by lactate estolides producing subtle fruit ester notes softer than acetate estolide banana or pear profiles
- **umami_aspartate_content** (d6): Concentration of free L-aspartate in the crumb, second most contributing free amino acid to savory sensation after glutamate, derived from proteolytic activity during lactobacillus fermentation.
- **umami_glutamate_content** (d6): Concentration of free L-glutamate in the crumb matrix arising from proteolytic breakdown of grain storage proteins during fermentation, the primary molecular driver of sourdough umami intensity.
- **umami_nucleotide_synergy** (d6): Enhancement of glutamate-driven umami perception through the synergistic interaction with 5'-ribonucleotides including IMP and GMP produced by microbial and flour enzymatic nucleic acid breakdown.
- **umami_peptide_fraction** (d6): Short-chain peptides and dipeptides in the crumb that contribute savory notes distinct from free amino acids, produced by partial proteolysis during extended fermentation.
- **umami_proteolytic_activity** (d6): Collective enzymatic hydrolysis of grain storage proteins into free amino acids and peptides, driven by both endogenous flour proteases and lactobacillus exoproteases during sourdough fermentation.
- **umami_receptor_activation** (d6): Binding of glutamate and aspartate to taste receptor type 1 member 1 and 3 complexes on the tongue and oral cavity, generating the savory taste signal that persists in sourdough aftertaste.
- **umami_flour_enzyme_contribution** (d7): Proteolytic breakdown of gliadin and glutenin in wheat flour by native flour endoproteases and exopeptidases during fermentation, independent of microbial proteases.

### from `sourdough_baking`
- **sourness_level** (d2): Intensity of acidic tang from lactobacillus fermentation ranging from mild to pronounced
- **acetic_acid** (d4): Sharp sour acid produced by lactobacillus in presence of oxygen creating tangy flavor
- **lactic_acid** (d4): Milder sour acid produced by lactobacillus contributing to bread tanginess
- **lactobacillus** (d4): Bacterial strains producing lactic and acetic acids that create sourdough tanginess
- **wild_yeast** (d4): Naturally occurring yeast strains captured from flour and the environment that ferment dough, providing rise without commercial yeast.

## CONSUMERS (what needs this)
`as_vigor_level`, `fermentation_onset_timing`, `microbial_activity_intensity`, `peak_fermentation_rate`, `starter_vitality`, `temperature_coefficient`, `wild_yeast`

---
*Projected from the `sourdough baking` KB (517 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*