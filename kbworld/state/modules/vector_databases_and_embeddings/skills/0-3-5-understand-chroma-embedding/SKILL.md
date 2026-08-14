---
name: 0.3.5-understand-chroma_embedding
description: "[0.3.5] A dense vector of floating-point numbers produced by an embedding function, representing the semantic position"
---

# understand-chroma_embedding

**CALL NUMBER:** `deep_vector_database.chroma_embedding`
**DEFINITION:** A dense vector of floating-point numbers produced by an embedding function, representing the semantic position of a document in high-dimensional space.

Invoke this skill to understand `chroma_embedding` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_vector_database`
- **chroma_embedding_function** (d1): A callable that converts raw input documents into embedding vectors; Chroma supports multiple backends (sentence-transformers, OpenAI, Cohere, etc.).

## CONSUMERS (what needs this)
`chroma_collection`, `chroma_document`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
