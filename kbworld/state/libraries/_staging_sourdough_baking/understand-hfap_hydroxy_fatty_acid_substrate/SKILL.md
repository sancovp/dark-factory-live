# understand-hfap_hydroxy_fatty_acid_substrate

**CALL NUMBER:** `deep_lactobacillus.hfap_hydroxy_fatty_acid_substrate : deep_fermentation(1)`
**DEFINITION:** The core hydroxy-bearing fatty acid molecule possessing a hydroxyl (-OH) functional group attached to its carbon chain, serving as the essential chemical moiety for estolide esterification in sourdough fermentation.

Invoke this skill to understand `hfap_hydroxy_fatty_acid_substrate` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_fermentation`
- **estolide_esterification_pathway** (d1): The biochemical condensation reaction between hydroxy fatty acids and fatty acids catalyzed by microbial esterases that produces estolide linkages and water as a byproduct during fermentation.

### from `deep_lactobacillus`
- **hfap_esterification_site** (d1): The nucleophilic hydroxyl (-OH) group on the hydroxy fatty acid that undergoes condensation with a fatty acid carboxyl group to form estolide_moiety ester bonds during fermentation.
- **hfap_fatty_acid_chain** (d1): The hydrophobic carbon backbone of the hydroxy fatty acid molecule, typically 16-18 carbons in length, that determines substrate specificity for estolide_esterification_pathway in sourdough matrix.

## CONSUMERS (what needs this)
`hfap_grain_lipid_oxidation`, `hfap_hydroperoxide_intermediate`, `hfap_linoleic_acid_derived`, `hfap_microbial_metabolism_source`, `hfap_oleic_acid_derived`

---
*Projected from the `sourdough baking` KB (510 concepts / 376 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*