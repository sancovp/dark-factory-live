---
name: 0.5.4-understand-hfap_lipid_substrate_pool
description: [0.5.4] Collective set of grain-derived unsaturated fatty acids including linoleic, oleic, and linolenic acids that se
---

# understand-hfap_lipid_substrate_pool

**CALL NUMBER:** `deep_lactobacillus.hfap_lipid_substrate_pool : deep_fermentation(1)`
**DEFINITION:** Collective set of grain-derived unsaturated fatty acids including linoleic, oleic, and linolenic acids that serve as the foundational pool for hydroxy_fatty_acid_substrate generation in sourdough fermentation.

Invoke this skill to understand `hfap_lipid_substrate_pool` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **grain_lipid_oxidation** (d1): The oxidative degradation of grain-derived unsaturated fatty acids (linoleic, oleic, and linolenic acids) driven by lipoxygenases and non-enzymatic free radical reactions during sourdough fermentation, producing hydroperoxides and reactive aldehydes that become substrates for hydroxy fatty acid biosynthesis.

### from `deep_fermentation`
- **estolide_esterification_pathway** (d3): The biochemical condensation reaction between hydroxy fatty acids and fatty acids catalyzed by microbial esterases that produces estolide linkages and water as a byproduct during fermentation.

### from `deep_lactobacillus`
- **hfap_linoleic_acid_derived** (d1): Hydroxy fatty acid precursor derived from linoleic acid (C18:2) through grain_lipid_oxidation or microbial_metabolism, providing the 9-hydroxy or 13-hydroxy positional isomers as estolide_esterification_pathway substrates.
- **hfap_oleic_acid_derived** (d1): Hydroxy fatty acid precursor derived from oleic acid (C18:1) through oxidative modification, yielding 9-hydroxy or 10-hydroxy positional isomers that participate in sourdough estolide formation.
- **hfap_hydroxy_fatty_acid_substrate** (d2): The core hydroxy-bearing fatty acid molecule possessing a hydroxyl (-OH) functional group attached to its carbon chain, serving as the essential chemical moiety for estolide esterification in sourdough fermentation.
- **hfap_esterification_site** (d3): The nucleophilic hydroxyl (-OH) group on the hydroxy fatty acid that undergoes condensation with a fatty acid carboxyl group to form estolide_moiety ester bonds during fermentation.
- **hfap_fatty_acid_chain** (d3): The hydrophobic carbon backbone of the hydroxy fatty acid molecule, typically 16-18 carbons in length, that determines substrate specificity for estolide_esterification_pathway in sourdough matrix.

---
*Projected from the `sourdough baking` KB (510 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
