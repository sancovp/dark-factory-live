---
name: 0.4.2-understand-dense_retrieval
description: "[0.4.2] Neural retrieval using learned embedding models to encode queries and documents into dense vectors for similar"
---

# understand-dense_retrieval

**CALL NUMBER:** `retrieval_augmented_generation_architecture_patt.dense_retrieval`
**DEFINITION:** Neural retrieval using learned embedding models to encode queries and documents into dense vectors for similarity search

Invoke this skill to understand `dense_retrieval` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `retrieval_augmented_generation_architecture_patt`
- **approximate_nearest_neighbor** (d1): Vector indexing technique trading exactness for speed: HNSW, IVF, or LSH structures enabling sub-linear retrieval at scale
- **cross_encoder_reranking** (d1): Two-pass retrieval: initial ANN retrieval followed by full cross-encoder scoring of candidate-document pairs for refined ranking
- **dense_passage_retriever** (d1): Bi-encoder model trained on query-passage pairs to produce jointly learned dense embeddings for retrieval
- **hybrid_rag** (d1): RAG combining dense vector retrieval with sparse lexical retrieval (BM25) to leverage both semantic similarity and exact keyword matching
- **hybrid_search** (d1): Retrieval combining multiple search paradigms (dense/sparse, vector/keyword) with score normalization or late fusion
- **colbert_style_retrieval** (d2): Late interaction retrieval: compute token-level similarity then aggregate for fine-grained relevance without full cross-encoding
- **retrieval_fusion** (d2): Combining results from multiple retrieval methods through Reciprocal Rank Fusion, Score Normalization, or learned weights
- **reciprocal_rank_fusion** (d3): Fusing ranked retrieval lists from multiple systems by reciprocal rank weighting to produce unified ranking

## CONSUMERS (what needs this)
`bi_encoder_retrieval`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
