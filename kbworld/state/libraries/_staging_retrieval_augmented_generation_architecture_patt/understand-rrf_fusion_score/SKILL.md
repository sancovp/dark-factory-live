# understand-rrf_fusion_score

**CALL NUMBER:** `deep_dense_retrieval.rrf_fusion_score`
**DEFINITION:** The sum of reciprocal rank values for a given document across all contributing rank lists; the document's position in the fused ranking is determined by descending fusion score.

Invoke this skill to understand `rrf_fusion_score` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_dense_retrieval`
- **rrf_final_ranking** (d1): The merged document list produced by sorting all candidates in descending order by their fusion scores, yielding a unified cross-system ranking that reflects all input retrieval evidence

## CONSUMERS (what needs this)
`rrf_document_candidate`, `rrf_fusion_score`, `rrf_reciprocal_rank_score`, `rrf_weighted_rrf`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*