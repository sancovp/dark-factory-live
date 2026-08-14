# understand-pinecone_query

**CALL NUMBER:** `deep_vector_database.pinecone_query`
**DEFINITION:** A read operation that returns approximate nearest neighbors to a query vector with optional metadata filtering and namespace scoping.

Invoke this skill to understand `pinecone_query` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **reads_from_pinecone_index** (d1): The data access relationship where fetch or query operations retrieve stored records from a Pinecone index by id or vector similarity.
- **receives_query_vector** (d1): The input relationship where a query operation accepts an embedding vector as the basis for nearest-neighbor similarity search.
- **returns_pinecone_similarity_score** (d1): The output relationship where a query operation yields relevance scores indicating how closely each result matches the query vector.
- **uses_approximate_nearest_neighbor_search** (d1): The algorithm relationship where a Pinecone query executes ANN search to efficiently return near neighbors rather than exact matches.

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*