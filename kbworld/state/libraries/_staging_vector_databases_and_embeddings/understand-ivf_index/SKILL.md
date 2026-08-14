# understand-ivf_index

**CALL NUMBER:** `vector_databases_and_embeddings.ivf_index`
**DEFINITION:** Inverted File Index; clusters vectors into Voronoi cells via k-means; search prunes to nearest centroids then scans partitions.

Invoke this skill to understand `ivf_index` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `vector_databases_and_embeddings`
- **indexing_strategy** (d1): Choice and configuration of ANN algorithm (HNSW, IVF, ANNOY, LSH) and its parameters (ef, nlist, nprobe) governing recall/speed trade-off.
- **product_quantization** (d1): A vector quantization technique that splits a high-dimensional vector into subvectors, independently quantizes each subvector, and concatenates codes to form a compact representation.
- **memory_footprint** (d2): RAM or VRAM required to hold index and vectors; quantization (PQ, int8) is the primary compression lever.

## CONSUMERS (what needs this)
`approximate_nearest_neighbor`, `idx_algorithm_selection`, `idx_hybrid_composition`, `idx_ivf_params`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*