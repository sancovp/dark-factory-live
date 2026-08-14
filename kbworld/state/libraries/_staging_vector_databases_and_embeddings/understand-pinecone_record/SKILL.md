# understand-pinecone_record

**CALL NUMBER:** `deep_vector_database.pinecone_record`
**DEFINITION:** A data unit in Pinecone containing id, dense vector values, optional sparse values, and key-value metadata.

Invoke this skill to understand `pinecone_record` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **belongs_to_pinecone_index** (d1): The containment relationship indicating a record resides within a specific Pinecone index for storage and retrieval.
- **belongs_to_pinecone_namespace** (d1): The tenancy relationship indicating a record is scoped to a particular namespace within a Pinecone index.
- **contains_pinecone_dense_vector** (d1): The composition relationship where a Pinecone record embeds dense vector values representing semantic embeddings for ANN search.
- **contains_pinecone_sparse_vector** (d1): The composition relationship where a Pinecone record optionally embeds sparse vector dimensions for hybrid dense-sparse retrieval.

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*