# understand-hnsw_index

**CALL NUMBER:** `vector_databases_and_embeddings.hnsw_index`
**DEFINITION:** Hierarchical Navigable Small World graph; layered skip-list + NN graph enabling logarithmic-layer traversal then constant-time local search.

Invoke this skill to understand `hnsw_index` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `vector_databases_and_embeddings`
- **indexing_strategy** (d1): Choice and configuration of ANN algorithm (HNSW, IVF, ANNOY, LSH) and its parameters (ef, nlist, nprobe) governing recall/speed trade-off.

## CONSUMERS (what needs this)
`approximate_nearest_neighbor`, `idx_algorithm_selection`, `idx_hnsw_params`, `idx_hybrid_composition`, `query_latency`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*