---
name: 0.4.3-understand-faiss
description: "[0.4.3] Meta's open-source C++/Python library for dense vector similarity search; implements IVF, PQ, HNSW, ONNG, and "
---

# understand-faiss

**CALL NUMBER:** `vector_databases_and_embeddings.faiss`
**DEFINITION:** Meta's open-source C++/Python library for dense vector similarity search; implements IVF, PQ, HNSW, ONNG, and GPU-accelerated kernels with optional 8-bit quantization.

Invoke this skill to understand `faiss` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `vector_databases_and_embeddings`
- **product_quantization** (d1): A vector quantization technique that splits a high-dimensional vector into subvectors, independently quantizes each subvector, and concatenates codes to form a compact representation.
- **scalar_quantization** (d1): Floating-point values mapped to low-precision (e.g. int8); reduces memory 4x with modest accuracy loss.
- **memory_footprint** (d2): RAM or VRAM required to hold index and vectors; quantization (PQ, int8) is the primary compression lever.

## CONSUMERS (what needs this)
`approximate_nearest_neighbor`, `idx_algorithm_selection`, `idx_faiss_index_factory`, `idx_gpu_acceleration`, `query_latency`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
