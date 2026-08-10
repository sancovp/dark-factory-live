---
name: 0.7.6-understand-baking
description: [0.7.6] Cooking dough in hot oven transforming it into bread through heat and chemical reactions
---

# understand-baking

**CALL NUMBER:** `sourdough_baking.baking : deep_fermentation(35), deep_lactobacillus(20), deep_baking(2)`
**DEFINITION:** Cooking dough in hot oven transforming it into bread through heat and chemical reactions

Invoke this skill to understand `baking` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **crumb_texture** (d2): The physical feel and structural quality of bread's interior ranging from fine and tender to coarse and chewy based on gluten development and fermentation.
- **crust_color** (d2): The brown coloration of bread's outer layer produced by Maillard reaction and caramelization during baking, ranging from pale gold to deep mahogany.
- **flavor_complexity** (d5): The depth and nuance of sourdough taste arising from multiple organic acids, esters, and alcohols produced during extended fermentation, creating tangy and complex notes.
- **banneton_flouring** (d7): Dusting the interior of a proofing basket with flour before placing shaped dough, preventing sticking and creating decorative flour patterns on the finished crust.

### from `deep_baking`
- **baking_duration** (d1): The total time bread spends in the oven during baking, typically 20-50 minutes depending on loaf size and oven temperature.
- **crumb_color** (d2): The visual shade of the bread interior ranging from pale ivory to deep golden depending on fermentation length, dough hydration, and baking time and temperature.

### from `deep_fermentation`
- **fermentation_byproducts** (d5): Compounds produced by microbial fermentation including carbon dioxide for dough rise, lactic and acetic acids for sour flavor, and alcohols for aroma.
- **aftertaste_tang_profile** (d6): The specific character of sour aftertaste sensations ranging from sharp and punchy to soft and creamy, shaped by the fc_acid_balance_ratio of persistent organic_acids.
- **carbon_dioxide** (d6): Gaseous byproduct of wild_yeast fermentation that provides dough rise and open crumb structure in sourdough bread.
- **ethanol** (d6): Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.
- **organic_acids** (d6): Carbon-chain acids produced by lactobacillus metabolism including lactic_acid and acetic_acid that determine sourness_level and contribute to flavor_complexity.
- **aroma_compounds** (d6): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **fc_acid_balance_ratio** (d6): The proportional ratio between acetic_acid and lactic_acid concentrations that fundamentally determines whether the tanginess is sharp and vinegary or soft and creamy
- **fc_aftertaste_development** (d6): The evolving and lingering flavor sensations that persist after swallowing, shaped by organic_acid persistence and aroma_compound retention in the crumb
- **fc_estolide_compounds** (d6): Aroma-active ester compounds produced by yeast and lactobacillus that contribute fruity, floral, and sometimes banana or pineapple notes to sourdough flavor complexity
- **fc_fermentation_depth** (d6): The cumulative flavor intensity arising from extended fermentation periods allowing progressive accumulation of organic_acids and aroma_compounds in the dough matrix
- **fc_higher_alcohols** (d6): Complex alcohol byproducts of wild_yeast fermentation beyond ethanol that add nutty, floral, and rozaceous nuances to the overall flavor profile
- **fc_maltolytic_notes** (d6): Caramel, toasty, and biscuit-like flavor compounds derived from enzymatic breakdown of grain starches during fermentation and Maillard reactions during baking
- **fc_tanginess_profile** (d6): The specific character and quality of sour notes in sourdough ranging from sharp and pungent to mild and creamy, determined by the balance between acetic acid sharpness and lactic acid softness
- **fc_volatile_esters** (d6): Aroma compounds formed through esterification reactions between organic_acids and ethanol during fermentation, contributing fruity and floral notes
- **fc_yeast_character** (d6): The bready, nutty, sometimes fruity or floral flavor notes contributed by wild_yeast metabolic activity including higher alcohols and their derivatives during fermentation
- **fce_microbial_source_spectrum** (d6): The range of estolide-producing organisms spanning wild_yeast esterases and lactobacillus acyl-CoA transferases each yielding distinct estolide profiles.
- **fermentation_vigor** (d6): Intensity and rate of the combined microbial fermentation process in sourdough, driven by wild_yeast gas production and lactobacillus acid generation, determining dough rise speed and flavor development timing.
- **fce_esterification_pathway** (d7): Biochemical condensation reaction between organic_acids and ethanol catalyzed by microbial esterase and acyltransferase enzymes during sourdough fermentation.
- **acid_retention_capacity** (d7): The ability of the crumb matrix to retain organic_acids such that they continue to stimulate taste receptors after the bread is consumed, influenced by crumb porosity and acid binding.
- **bitterness_trail** (d7): Any lingering bitter notes in the aftertaste, often associated with certain organic_acids or fermentation byproducts that persist due to their solubility characteristics.
- **tanginess_linger** (d7): The duration and intensity of sour taste sensations that persist in the mouth after swallowing, determined by organic_acid type and concentration.
- **fragrance_dwell** (d7): The lingering presence of fruity, floral, or ester-derived aroma notes in the aftertaste, attributed to fc_volatile_esters and fc_estolide_compounds with low volatility.
- **retronasal_aroma** (d7): Volatile aroma compounds released in the mouth after swallowing that travel to the olfactory receptors via the retronasal passage, forming a key component of sourdough aftertaste.
- **volatile_release_rate** (d7): The speed at which aroma_compounds evaporate and reach olfactory receptors in the mouth after swallowing, determining whether aftertaste aromatics are fleeting or prolonged.
- **aftertaste_sensory_profile** (d7): The composite quality of lingering flavor sensations after swallowing sourdough, encompassing taste, aroma, and mouthfeel dimensions that evolve over time.

### from `deep_lactobacillus`
- **lactate_estolide_formation_pathway** (d6): Biochemical condensation pathway where lactobacillus lactic_acid reacts with ethanol via acyl-CoA transferase enzymes to form lactate estolide linkages
- **umami_microbial_protease_contribution** (d6): Proteolytic enzymes secreted by lactobacillus strains including aminopeptidases and endopeptidases that hydrolyze flour proteins into free amino acids contributing to umami sensation.
- **umami_savory_character** (d7): The specific quality of savory, broth-like, meaty, or full-bodied taste notes in sourdough arising from glutamate concentration and nucleotide synergy, distinct from sweet, sour, salty, and bitter dimensions.
- **lactic_acid_esterification_mechanism** (d7): Specific biochemical reaction mechanism by which lactic_acid carboxylic group bonds with ethanol hydroxyl group forming ester bonds characteristic of lactate estolides
- **umami_aftertaste_duration** (d8): The temporal persistence of savory taste sensation after swallowing sourdough, determined by retention of free amino acids and peptides in the crumb matrix and their continued release during oral clearance.
- **lactate_estolide_volatility_profile** (d8): Evaporation rate and atmospheric persistence characteristics of lactate estolide aroma compounds determining whether buttery-creamy notes are fleeting or lingering
- **lactate_estolide_sensory_profile** (d8): Composite sensory character of lactate estolides encompassing buttery_note_contribution creamy_note_contribution and mild_fruity_note_contribution defining their distinct flavor identity
- **lactate_estolide_odor_threshold** (d8): Concentration at which specific lactate estolide compounds become detectable by human olfaction varying by carbon chain length and esterification degree
- **sharpness_comparison_to_acetate** (d8): Relative sensory differentiation where lactate estolides produce softer rounded tang versus acetate estolides producing sharper punchier notes
- **lactate_estolide_carbon_chain_variants** (d8): Structural variations in lactate estolides defined by carbon chain length of the lactic_acid moiety determining aroma intensity and character
- **buttery_note_contribution** (d9): Sensory attribute contributed by lactate estolides producing rich buttercream flavor impressions distinct from dairy-free sharp acetate estolides
- **creamy_note_contribution** (d9): Sensory attribute contributed by lactate estolides producing smooth mouthfeel impressions and lactone-like creamy flavor sensations
- **mild_fruity_note_contribution** (d9): Sensory attribute contributed by lactate estolides producing subtle fruit ester notes softer than acetate estolide banana or pear profiles
- **umami_aspartate_content** (d9): Concentration of free L-aspartate in the crumb, second most contributing free amino acid to savory sensation after glutamate, derived from proteolytic activity during lactobacillus fermentation.
- **umami_glutamate_content** (d9): Concentration of free L-glutamate in the crumb matrix arising from proteolytic breakdown of grain storage proteins during fermentation, the primary molecular driver of sourdough umami intensity.
- **umami_nucleotide_synergy** (d9): Enhancement of glutamate-driven umami perception through the synergistic interaction with 5'-ribonucleotides including IMP and GMP produced by microbial and flour enzymatic nucleic acid breakdown.
- **umami_peptide_fraction** (d9): Short-chain peptides and dipeptides in the crumb that contribute savory notes distinct from free amino acids, produced by partial proteolysis during extended fermentation.
- **umami_proteolytic_activity** (d9): Collective enzymatic hydrolysis of grain storage proteins into free amino acids and peptides, driven by both endogenous flour proteases and lactobacillus exoproteases during sourdough fermentation.
- **umami_receptor_activation** (d9): Binding of glutamate and aspartate to taste receptor type 1 member 1 and 3 complexes on the tongue and oral cavity, generating the savory taste signal that persists in sourdough aftertaste.
- **umami_flour_enzyme_contribution** (d10): Proteolytic breakdown of gliadin and glutenin in wheat flour by native flour endoproteases and exopeptidases during fermentation, independent of microbial proteases.

### from `sourdough_baking`
- **baking_temperature** (d1): Oven heat setting typically between 450-500F for home sourdough baking
- **crumb** (d1): The interior crumb structure of bread characterized by hole size, distribution, tenderness, and openness ranging from tight and dense to open and airy.
- **crust** (d1): The baked outer layer of bread formed by Maillard reaction and caramelization; texture ranges from thin and crispy to thick and chewy based on hydration and baking method.
- **dutch_oven** (d1): Heavy lidded pot used to bake sourdough that traps steam from dough moisture, creating professional results without an oven steam injection system.
- **internal_temperature** (d1): Bread center temperature (typically 195-210F/90-99C) indicating doneness; lower temps leave gummy crumb.
- **lid_removal** (d1): Taking Dutch oven lid off mid-bake to release steam and finish crust coloring
- **oven_spring** (d1): Rapid oven rise occurring in the first 10-15 minutes of baking due to yeast activity, gas expansion, and steam; creates open crumb and dramatic ear.
- **steam_production** (d1): Water vapor released in oven creating humid environment for optimal crust development
- **bread_volume** (d2): Total size and height of finished loaf indicating proper fermentation and oven spring
- **crumb_structure** (d2): Internal architecture of bread defined by bubble size, distribution, and tenderness
- **crust_texture** (d2): External characteristics of crust from chewy and thick to thin and crispy
- **ear** (d2): The lifted crust edge formed from scoring that rises dramatically during oven spring; prized aesthetic and texture element in artisan sourdough.
- **maillard_reaction** (d2): Chemical reaction between amino acids and sugars at high temperatures creating brown crust color and complex savory flavors.
- **dough_temperature** (d2): Target temperature of mixed dough (typically 75-80F/24-27C) ensuring predictable fermentation timing regardless of room conditions.
- **gluten_development** (d2): Process of hydrating and aligning gluten proteins through mixing, folding, or autolyse to create strong extensible dough.
- **scoring** (d2): Shallow cuts made on proofed dough before baking to control oven spring direction, create visual patterns, and allow steam to escape during baking.
- **bulk_fermentation** (d3): Primary fermentation phase where the mixed dough rests and ferments before shaping; time and temperature control gas production and flavor development.
- **fermentation_temperature** (d3): Environmental temperature during bulk and final proof that directly controls fermentation speed; warmer accelerates, cooler slows.
- **dough_consistency** (d3): Viscosity and handling quality from soft and extensible to firm and tight
- **lame** (d3): Sharp curved blade used for scoring bread, typically with a wooden handle, that creates clean precise cuts for ear formation.
- **scoring_angle** (d3): Blade orientation relative to dough surface affecting ear formation and rise pattern
- **fermentation** (d4): Metabolic process where microbes convert sugars to CO2 for rise and acids for sour flavor
- **fold_count** (d4): Number of stretch and fold repetitions during bulk fermentation for gluten development
- **proofing** (d4): Final fermentation phase where shaped dough rises before baking
- **stretch_and_fold** (d4): Method of periodically stretching dough quarters and folding them into the center during bulk fermentation to develop structure without degassing.

---
*Projected from the `sourdough baking` KB (517 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
