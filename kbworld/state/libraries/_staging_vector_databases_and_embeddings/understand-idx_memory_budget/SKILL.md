# understand-idx_memory_budget

**CALL NUMBER:** `deep_nearest_neighbor_sea.idx_memory_budget : vector_databases_and_embeddings(3)`
**DEFINITION:** Available RAM or VRAM for index and raw vectors constraining quantization choices and index density

Invoke this skill to understand `idx_memory_budget` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `vector_databases_and_embeddings`
- **memory_footprint** (d1): RAM or VRAM required to hold index and vectors; quantization (PQ, int8) is the primary compression lever.
- **product_quantization** (d1): A vector quantization technique that splits a high-dimensional vector into subvectors, independently quantizes each subvector, and concatenates codes to form a compact representation.
- **scalar_quantization** (d1): Floating-point values mapped to low-precision (e.g. int8); reduces memory 4x with modest accuracy loss.

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*