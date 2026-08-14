---
name: 0.3.1-understand-chroma_collection
description: [0.3.1] A named namespace within Chroma that stores embeddings, associated documents, metadata, and IDs as an isolated
---

# understand-chroma_collection

**CALL NUMBER:** `deep_vector_database.chroma_collection`
**DEFINITION:** A named namespace within Chroma that stores embeddings, associated documents, metadata, and IDs as an isolated group.

Invoke this skill to understand `chroma_collection` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_vector_database`
- **chroma_document** (d1): The raw text or payload string that is embedded and stored alongside its vector representation in a collection.
- **chroma_embedding** (d1): A dense vector of floating-point numbers produced by an embedding function, representing the semantic position of a document in high-dimensional space.
- **chroma_entry_id** (d1): A unique identifier string assigned to each embedded document within a collection; used for targeted get/delete operations.
- **chroma_filter** (d1): A metadata predicate applied at query time to restrict which entries are considered during approximate nearest-neighbor search.
- **chroma_metadata** (d1): Structured key-value attributes attached to an embedding entry; enables filtering and payload queries at query time.
- **chroma_embedding_function** (d2): A callable that converts raw input documents into embedding vectors; Chroma supports multiple backends (sentence-transformers, OpenAI, Cohere, etc.).

## CONSUMERS (what needs this)
`chroma_persistence`, `chroma_query`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
