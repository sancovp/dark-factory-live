---
name: 0.2.2-understand-colbert_approximate_search
description: [0.2.2] Approximate nearest neighbor indexing on per-token document embeddings enabling efficient retrieval of candida
---

# understand-colbert_approximate_search

**CALL NUMBER:** `deep_dense_retrieval.colbert_approximate_search : retrieval_augmented_generation_architecture_patt(5)`
**DEFINITION:** Approximate nearest neighbor indexing on per-token document embeddings enabling efficient retrieval of candidate documents before late interaction re-scoring.

Invoke this skill to understand `colbert_approximate_search` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_dense_retrieval`
- **colbert_document_encoder** (d1): Encoder producing per-token document embeddings from document passages, typically run offline and indexed for fast retrieval against query embeddings.
- **colbert_representation_rank** (d2): Rank dimension of per-token embeddings determining expressiveness of token-level similarity computation in late interaction framework.

### from `retrieval_augmented_generation_architecture_patt`
- **approximate_nearest_neighbor** (d1): Vector indexing technique trading exactness for speed: HNSW, IVF, or LSH structures enabling sub-linear retrieval at scale
- **hybrid_search** (d1): Retrieval combining multiple search paradigms (dense/sparse, vector/keyword) with score normalization or late fusion
- **colbert_style_retrieval** (d2): Late interaction retrieval: compute token-level similarity then aggregate for fine-grained relevance without full cross-encoding
- **retrieval_fusion** (d2): Combining results from multiple retrieval methods through Reciprocal Rank Fusion, Score Normalization, or learned weights
- **reciprocal_rank_fusion** (d3): Fusing ranked retrieval lists from multiple systems by reciprocal rank weighting to produce unified ranking

## CONSUMERS (what needs this)
`colbert_re_reranking`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
