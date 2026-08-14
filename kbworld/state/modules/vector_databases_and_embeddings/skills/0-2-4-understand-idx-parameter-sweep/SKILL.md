---
name: 0.2.4-understand-idx_parameter_sweep
description: "[0.2.4] Systematic exploration of parameter space to find optimal recall speed trade off for given constraints"
---

# understand-idx_parameter_sweep

**CALL NUMBER:** `deep_nearest_neighbor_sea.idx_parameter_sweep : vector_databases_and_embeddings(8)`
**DEFINITION:** Systematic exploration of parameter space to find optimal recall speed trade off for given constraints

Invoke this skill to understand `idx_parameter_sweep` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_nearest_neighbor_sea`
- **idx_query_latency_budget** (d1): Maximum acceptable query response time constraining algorithm selection and pruning aggressiveness
- **idx_recall_target** (d1): Desired fraction of true nearest neighbors returned governing aggressiveness of search pruning and parameter tuning

### from `vector_databases_and_embeddings`
- **approximate_nearest_neighbor** (d2): An ANN algorithm that trades exact recall for sub-linear query time by probabilistically organizing the embedding space into clusters or graphs.
- **faiss** (d3): Meta's open-source C++/Python library for dense vector similarity search; implements IVF, PQ, HNSW, ONNG, and GPU-accelerated kernels with optional 8-bit quantization.
- **hnsw_index** (d3): Hierarchical Navigable Small World graph; layered skip-list + NN graph enabling logarithmic-layer traversal then constant-time local search.
- **ivf_index** (d3): Inverted File Index; clusters vectors into Voronoi cells via k-means; search prunes to nearest centroids then scans partitions.
- **product_quantization** (d4): A vector quantization technique that splits a high-dimensional vector into subvectors, independently quantizes each subvector, and concatenates codes to form a compact representation.
- **scalar_quantization** (d4): Floating-point values mapped to low-precision (e.g. int8); reduces memory 4x with modest accuracy loss.
- **indexing_strategy** (d4): Choice and configuration of ANN algorithm (HNSW, IVF, ANNOY, LSH) and its parameters (ef, nlist, nprobe) governing recall/speed trade-off.
- **memory_footprint** (d5): RAM or VRAM required to hold index and vectors; quantization (PQ, int8) is the primary compression lever.

## CONSUMERS (what needs this)
`idx_workload_profiling`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
