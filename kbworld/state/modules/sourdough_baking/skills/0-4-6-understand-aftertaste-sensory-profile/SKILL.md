---
name: 0.4.6-understand-aftertaste_sensory_profile
description: "[0.4.6] The composite quality of lingering flavor sensations after swallowing sourdough, encompassing taste, aroma, an"
---

# understand-aftertaste_sensory_profile

**CALL NUMBER:** `deep_fermentation.aftertaste_sensory_profile : deep_lactobacillus(16)`
**DEFINITION:** The composite quality of lingering flavor sensations after swallowing sourdough, encompassing taste, aroma, and mouthfeel dimensions that evolve over time.

Invoke this skill to understand `aftertaste_sensory_profile` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **bitterness_trail** (d1): Any lingering bitter notes in the aftertaste, often associated with certain organic_acids or fermentation byproducts that persist due to their solubility characteristics.
- **mouthfeel_aftereffect** (d1): The tactile sensation that persists after swallowing sourdough, including astringency, dryness, or coating quality left by the crumb structure and fermentation compounds.
- **retronasal_aroma** (d1): Volatile aroma compounds released in the mouth after swallowing that travel to the olfactory receptors via the retronasal passage, forming a key component of sourdough aftertaste.
- **tanginess_linger** (d1): The duration and intensity of sour taste sensations that persist in the mouth after swallowing, determined by organic_acid type and concentration.
- **umami_sensation** (d1): Savory or broth-like lingering taste notes in sourdough aftertaste, contributed by amino acids and peptides from proteolytic activity during fermentation.

### from `deep_lactobacillus`
- **lactate_estolide_sensory_profile** (d1): Composite sensory character of lactate estolides encompassing buttery_note_contribution creamy_note_contribution and mild_fruity_note_contribution defining their distinct flavor identity
- **buttery_note_contribution** (d2): Sensory attribute contributed by lactate estolides producing rich buttercream flavor impressions distinct from dairy-free sharp acetate estolides
- **creamy_note_contribution** (d2): Sensory attribute contributed by lactate estolides producing smooth mouthfeel impressions and lactone-like creamy flavor sensations
- **mild_fruity_note_contribution** (d2): Sensory attribute contributed by lactate estolides producing subtle fruit ester notes softer than acetate estolide banana or pear profiles
- **umami_aftertaste_duration** (d2): The temporal persistence of savory taste sensation after swallowing sourdough, determined by retention of free amino acids and peptides in the crumb matrix and their continued release during oral clearance.
- **umami_aspartate_content** (d2): Concentration of free L-aspartate in the crumb, second most contributing free amino acid to savory sensation after glutamate, derived from proteolytic activity during lactobacillus fermentation.
- **umami_glutamate_content** (d2): Concentration of free L-glutamate in the crumb matrix arising from proteolytic breakdown of grain storage proteins during fermentation, the primary molecular driver of sourdough umami intensity.
- **umami_nucleotide_synergy** (d2): Enhancement of glutamate-driven umami perception through the synergistic interaction with 5'-ribonucleotides including IMP and GMP produced by microbial and flour enzymatic nucleic acid breakdown.
- **umami_peptide_fraction** (d2): Short-chain peptides and dipeptides in the crumb that contribute savory notes distinct from free amino acids, produced by partial proteolysis during extended fermentation.
- **umami_proteolytic_activity** (d2): Collective enzymatic hydrolysis of grain storage proteins into free amino acids and peptides, driven by both endogenous flour proteases and lactobacillus exoproteases during sourdough fermentation.
- **umami_receptor_activation** (d2): Binding of glutamate and aspartate to taste receptor type 1 member 1 and 3 complexes on the tongue and oral cavity, generating the savory taste signal that persists in sourdough aftertaste.
- **umami_savory_character** (d2): The specific quality of savory, broth-like, meaty, or full-bodied taste notes in sourdough arising from glutamate concentration and nucleotide synergy, distinct from sweet, sour, salty, and bitter dimensions.
- **lactate_estolide_odor_threshold** (d3): Concentration at which specific lactate estolide compounds become detectable by human olfaction varying by carbon chain length and esterification degree
- **lactate_estolide_volatility_profile** (d3): Evaporation rate and atmospheric persistence characteristics of lactate estolide aroma compounds determining whether buttery-creamy notes are fleeting or lingering
- **umami_flour_enzyme_contribution** (d3): Proteolytic breakdown of gliadin and glutenin in wheat flour by native flour endoproteases and exopeptidases during fermentation, independent of microbial proteases.
- **umami_microbial_protease_contribution** (d3): Proteolytic enzymes secreted by lactobacillus strains including aminopeptidases and endopeptidases that hydrolyze flour proteins into free amino acids contributing to umami sensation.

## CONSUMERS (what needs this)
`fc_aftertaste_development`, `fc_higher_alcohols`

---
*Projected from the `sourdough baking` KB (517 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
