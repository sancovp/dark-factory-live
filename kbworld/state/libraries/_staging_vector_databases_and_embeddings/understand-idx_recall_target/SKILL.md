# understand-idx_recall_target

**CALL NUMBER:** `deep_nearest_neighbor_sea.idx_recall_target : vector_databases_and_embeddings(8)`
**DEFINITION:** Desired fraction of true nearest neighbors returned governing aggressiveness of search pruning and parameter tuning

Invoke this skill to understand `idx_recall_target` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `vector_databases_and_embeddings`
- **approximate_nearest_neighbor** (d1): An ANN algorithm that trades exact recall for sub-linear query time by probabilistically organizing the embedding space into clusters or graphs.
- **faiss** (d2): Meta's open-source C++/Python library for dense vector similarity search; implements IVF, PQ, HNSW, ONNG, and GPU-accelerated kernels with optional 8-bit quantization.
- **hnsw_index** (d2): Hierarchical Navigable Small World graph; layered skip-list + NN graph enabling logarithmic-layer traversal then constant-time local search.
- **ivf_index** (d2): Inverted File Index; clusters vectors into Voronoi cells via k-means; search prunes to nearest centroids then scans partitions.
- **product_quantization** (d3): A vector quantization technique that splits a high-dimensional vector into subvectors, independently quantizes each subvector, and concatenates codes to form a compact representation.
- **scalar_quantization** (d3): Floating-point values mapped to low-precision (e.g. int8); reduces memory 4x with modest accuracy loss.
- **indexing_strategy** (d3): Choice and configuration of ANN algorithm (HNSW, IVF, ANNOY, LSH) and its parameters (ef, nlist, nprobe) governing recall/speed trade-off.
- **memory_footprint** (d4): RAM or VRAM required to hold index and vectors; quantization (PQ, int8) is the primary compression lever.

## CONSUMERS (what needs this)
`idx_parameter_sweep`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*