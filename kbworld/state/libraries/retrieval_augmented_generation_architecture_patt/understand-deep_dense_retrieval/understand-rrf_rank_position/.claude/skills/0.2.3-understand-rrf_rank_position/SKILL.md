---
name: 0.2.3-understand-rrf_rank_position
description: [0.2.3] The integer position of an item within a rank list, starting at 1 for the highest-scoring result; used as the 
---

# understand-rrf_rank_position

**CALL NUMBER:** `deep_dense_retrieval.rrf_rank_position`
**DEFINITION:** The integer position of an item within a rank list, starting at 1 for the highest-scoring result; used as the denominator in reciprocal rank computation.

Invoke this skill to understand `rrf_rank_position` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_dense_retrieval`
- **rrf_constant_k** (d1): A positive smoothing constant (conventional value 60) added to each rank position before taking the reciprocal, preventing division by zero and dampening sensitivity to high ranks for stable fusion scoring
- **rrf_reciprocal_rank_score** (d1): The per-system score for a document computed as 1 divided by the sum of rank position and constant k, yielding a value in (0, 1/k] that decays with worsening rank
- **rrf_fusion_score** (d2): The sum of reciprocal rank values for a given document across all contributing rank lists; the document's position in the fused ranking is determined by descending fusion score.
- **rrf_final_ranking** (d3): The merged document list produced by sorting all candidates in descending order by their fusion scores, yielding a unified cross-system ranking that reflects all input retrieval evidence

## CONSUMERS (what needs this)
`rrf_normalization_preprocessing`, `rrf_ranked_list`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
