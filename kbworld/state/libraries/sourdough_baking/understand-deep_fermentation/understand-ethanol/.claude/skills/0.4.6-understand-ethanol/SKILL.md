---
name: 0.4.6-understand-ethanol
description: [0.4.6] Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to 
---

# understand-ethanol

**CALL NUMBER:** `deep_fermentation.ethanol`
**DEFINITION:** Alcohol produced by wild_yeast during anaerobic fermentation that evaporates during baking and contributes to flavor_complexity development.

Invoke this skill to understand `ethanol` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **estolide_esterification_catalysis** (d1): The enzyme-mediated chemical reaction combining ethanol with organic_acids to form estolide_compounds as esters, catalyzed by microbial esterases during fermentation that enables the conversion of alcohol and acid precursors into fruity and floral aroma molecules.
- **estolide_retention_in_crumb** (d3): The physical trapping and chemical binding of estolide_compounds within the gluten-starch matrix of bread crumb during baking, enabling their gradual volatilization during mastication to extend fruity and floral aftertaste perception.

### from `deep_fermentation`
- **aroma_compounds** (d1): Volatile fermentation byproducts including alcohols and esters that create the aromatic profile of sourdough.
- **sweet_tail** (d1): Subtle perception of sweetness at the tail end of aftertaste, arising from residual maltose未被发酵and mmaltolytic_note generation during baking that lingers as palate sensation.
- **aroma_retention_capacity** (d2): The extent to which aroma_compounds become trapped within the bread crumb structure during baking and cooling, enabling continued volatilization in the mouth during and after swallowing.
- **lingering_sensation_profile** (d3): The specific sequence and combination of taste impressions that unfold in the mouth after swallowing, including sour, bitter, sweet, and umami elements in their temporal order.
- **temporal_aftertaste_curve** (d3): The time-based trajectory of aftertaste sensation intensity from moment of swallowing through gradual decay to baseline, characterized by rise, peak, plateau, and fade phases.

## CONSUMERS (what needs this)
`fc_fermentation_depth`, `fermentation_byproducts`, `flavor_complexity`, `wild_yeast`

---
*Projected from the `sourdough baking` KB (546 concepts / 365 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
