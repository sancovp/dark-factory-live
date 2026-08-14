---
name: 0.3.2-understand-chroma_query
description: "[0.3.2] A search request containing a query vector (or text to embed) plus optional top-k and metadata filter paramete"
---

# understand-chroma_query

**CALL NUMBER:** `deep_vector_database.chroma_query`
**DEFINITION:** A search request containing a query vector (or text to embed) plus optional top-k and metadata filter parameters.

Invoke this skill to understand `chroma_query` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_vector_database`
- **chroma_collection** (d1): A named namespace within Chroma that stores embeddings, associated documents, metadata, and IDs as an isolated group.
- **chroma_distance_metric** (d1): The similarity measure used for nearest-neighbor ranking; Chroma supports cosine, euclidean, and dot product distances.
- **chroma_filter** (d1): A metadata predicate applied at query time to restrict which entries are considered during approximate nearest-neighbor search.
- **chroma_document** (d2): The raw text or payload string that is embedded and stored alongside its vector representation in a collection.
- **chroma_embedding** (d2): A dense vector of floating-point numbers produced by an embedding function, representing the semantic position of a document in high-dimensional space.
- **chroma_entry_id** (d2): A unique identifier string assigned to each embedded document within a collection; used for targeted get/delete operations.
- **chroma_metadata** (d2): Structured key-value attributes attached to an embedding entry; enables filtering and payload queries at query time.
- **chroma_embedding_function** (d3): A callable that converts raw input documents into embedding vectors; Chroma supports multiple backends (sentence-transformers, OpenAI, Cohere, etc.).

## CONSUMERS (what needs this)
`chroma_result_set`

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
