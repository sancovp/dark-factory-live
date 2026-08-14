---
name: 0.4.6-understand-vector_database
description: [0.4.6] Storage system indexing embeddings for similarity search; backbone of RAG. Examples: Pinecone, Weaviate, Chrom
---

# understand-vector_database

**CALL NUMBER:** `llm_memory_and_context_engineering.vector_database : deep_long_term_memory(2)`
**DEFINITION:** Storage system indexing embeddings for similarity search; backbone of RAG. Examples: Pinecone, Weaviate, Chroma, FAISS. Enables retrieval from vast document collections.

Invoke this skill to understand `vector_database` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_long_term_memory`
- **em_significance_rank** (d3): Ordering structure by event importance or impact; enables retrieval by significance rather than recency.
- **em_temporal_index** (d3): Organizational structure mapping events to time ranges; enables retrieval by temporal proximity.

### from `llm_memory_and_context_engineering`
- **approximate_nearest_neighbor** (d1): Fast retrieval of roughly similar vectors accepting some error; enables scaling vector_database beyond exact search limits
- **chunking_strategy** (d1): How documents are split into retrieval units; choices affect recall/precision: fixed-size, semantic (by sentences/paragraphs), recursive, or agentic splitting.
- **cosine_similarity** (d1): A similarity measure between embedding vectors based on the cosine of the angle between them; invariant to vector magnitude
- **embedding_dimensionality** (d1): Number of dimensions in the embedding_space; higher captures more nuance but increases storage and retrieval_cost
- **embedding_model** (d1): A model trained to produce text_embedding vectors; may be a general encoder like CLIP, a domain-specific encoder, or a late-intercept from an LLM
- **hierarchical_chunking** (d1): Recursive splitting of text into nested chunks enabling multi-granularity retrieval from summary to detail
- **locality_sensitive_hashing** (d1): Hashing scheme preserving similarity relationships; used in approximate_nearest_neighbor for fast vector_database queries
- **overlapping_chunks** (d1): Chunking strategy where adjacent chunks share boundary tokens to prevent information loss at chunk_boundaries
- **semantic_similarity** (d1): Measure of meaning overlap between two text fragments in embedding_space; the basis for associative_memory retrieval
- **context_fidelity** (d2): The accuracy with which context content reflects ground truth; low fidelity leads to hallucinated reasoning from corrupted context
- **memory_retrieval** (d2): The act of fetching stored memory entries — by semantic similarity, keyword, metadata, or temporal proximity — to include in context
- **associative_memory** (d2): Recall triggered by related concepts; attention mechanism is a form of content-addressable associative memory enabling retrieval by similarity.

## CONSUMERS (what needs this)
`long_term_memory`, `retrieval_augmented_generation`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
