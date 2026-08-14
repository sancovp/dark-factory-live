---
name: 0.2.1-understand-idx_algorithm_selection
description: "[0.2.1] Choice among ANN index types HNSW IVF ANNOY LSH determined by data scale query patterns and accuracy requireme"
---

# understand-idx_algorithm_selection

**CALL NUMBER:** `deep_nearest_neighbor_sea.idx_algorithm_selection : vector_databases_and_embeddings(7)`
**DEFINITION:** Choice among ANN index types HNSW IVF ANNOY LSH determined by data scale query patterns and accuracy requirements

Invoke this skill to understand `idx_algorithm_selection` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `vector_databases_and_embeddings`
- **faiss** (d1): Meta's open-source C++/Python library for dense vector similarity search; implements IVF, PQ, HNSW, ONNG, and GPU-accelerated kernels with optional 8-bit quantization.
- **hnsw_index** (d1): Hierarchical Navigable Small World graph; layered skip-list + NN graph enabling logarithmic-layer traversal then constant-time local search.
- **ivf_index** (d1): Inverted File Index; clusters vectors into Voronoi cells via k-means; search prunes to nearest centroids then scans partitions.
- **product_quantization** (d2): A vector quantization technique that splits a high-dimensional vector into subvectors, independently quantizes each subvector, and concatenates codes to form a compact representation.
- **scalar_quantization** (d2): Floating-point values mapped to low-precision (e.g. int8); reduces memory 4x with modest accuracy loss.
- **indexing_strategy** (d2): Choice and configuration of ANN algorithm (HNSW, IVF, ANNOY, LSH) and its parameters (ef, nlist, nprobe) governing recall/speed trade-off.
- **memory_footprint** (d3): RAM or VRAM required to hold index and vectors; quantization (PQ, int8) is the primary compression lever.

## CONSUMERS (what needs this)
`idx_workload_profiling`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
