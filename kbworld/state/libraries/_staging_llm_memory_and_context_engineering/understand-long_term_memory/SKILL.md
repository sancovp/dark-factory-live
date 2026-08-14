# understand-long_term_memory

**CALL NUMBER:** `llm_memory_and_context_engineering.long_term_memory : deep_long_term_memory(14)`
**DEFINITION:** Information persisted across sessions, tasks, or deployments; requires external storage and retrieval mechanisms since it cannot fit in context_window

Invoke this skill to understand `long_term_memory` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_long_term_memory`
- **em_episode_marker** (d2): Signal indicating episode boundaries: new session start, task boundary, or conversational turn demarcation.
- **em_event** (d2): A discrete unit of experience stored in episodic memory — a single interaction, task completion, or notable outcome.
- **em_significance_rank** (d2): Ordering structure by event importance or impact; enables retrieval by significance rather than recency.
- **em_temporal_index** (d2): Organizational structure mapping events to time ranges; enables retrieval by temporal proximity.
- **em_experience_sequence** (d2): An ordered collection of events forming a coherent experiential arc; the episodic unit of storage.
- **em_salience_weight** (d2): Numeric value indicating how memorable or significant an event is; influences consolidation priority and retrieval ranking.
- **em_recency_decay** (d2): Algorithm for reducing salience weights of older events over time; models forgetting in episodic memory.
- **kg_inference** (d2): Deriving new kg_triple entries from existing ones through rule application or traversal over the kg_ontology (e.g., transitivity of is_a)
- **kg_traversal** (d2): Navigating the knowledge_graph along kg_relationship edges to discover connected kg_entities; the fundamental operation enabling associative retrieval
- **em_context_bundle** (d3): The surrounding context of an event including user inputs, system responses, and environmental state at the time.
- **em_interaction_record** (d3): Structured log of the exchange pairs (prompt/response) comprising an event.
- **em_outcome** (d3): The result or consequence of an event — success, failure, or partial completion — recorded for outcome-based retrieval.
- **em_state_snapshot** (d3): Captured system state (context window contents, active variables, user profile) at the moment of an event.
- **em_timestamp** (d3): Temporal marker indicating when an event occurred; enables chronological ordering of episodic entries.

### from `llm_memory_and_context_engineering`
- **episodic_memory** (d1): Memory storing discrete experiences or events — specific interactions,完成任务, or notable outcomes — organized chronologically or by significance
- **knowledge_graph** (d1): A graph-structured representation of entities and their relationships; used as a structured form of semantic_memory with traversable edges
- **memory_audit** (d1): Systematic review of stored memories for accuracy, relevance, and compliance; governance practice for long_term_memory systems
- **memory_capacity** (d1): Maximum storable items in a memory system; bounded by context_length for working_memory and storage size for long_term_memory
- **memory_consolidation** (d1): The process of transforming short-term memory representations into longer-term storage; converting ephemeral state to persistent records
- **memory_invalidation** (d1): Removing or updating outdated memories; necessary when world_model facts change and stored memories become incorrect
- **memory_persistence** (d1): How long memory survives; session memory (within conversation), user memory (across sessions), or permanent memory (until explicitly deleted).
- **memory_poisoning** (d1): Corruption of long_term_memory stores with false or harmful content; defense requires verification and source attribution
- **memory_retrieval** (d1): The act of fetching stored memory entries — by semantic similarity, keyword, metadata, or temporal proximity — to include in context
- **semantic_memory** (d1): Memory storing general world knowledge, facts, and concepts rather than specific personal experiences; queried via retrieval for grounding
- **semantic_network** (d1): Graph of concepts connected by typed edges; models can store and traverse this structure for relational reasoning
- **vector_database** (d1): Storage system indexing embeddings for similarity search; backbone of RAG. Examples: Pinecone, Weaviate, Chroma, FAISS. Enables retrieval from vast document collections.
- **semantic_similarity** (d2): Measure of meaning overlap between two text fragments in embedding_space; the basis for associative_memory retrieval
- **approximate_nearest_neighbor** (d2): Fast retrieval of roughly similar vectors accepting some error; enables scaling vector_database beyond exact search limits
- **chunking_strategy** (d2): How documents are split into retrieval units; choices affect recall/precision: fixed-size, semantic (by sentences/paragraphs), recursive, or agentic splitting.
- **cosine_similarity** (d2): A similarity measure between embedding vectors based on the cosine of the angle between them; invariant to vector magnitude
- **embedding_dimensionality** (d2): Number of dimensions in the embedding_space; higher captures more nuance but increases storage and retrieval_cost
- **embedding_model** (d2): A model trained to produce text_embedding vectors; may be a general encoder like CLIP, a domain-specific encoder, or a late-intercept from an LLM
- **hierarchical_chunking** (d2): Recursive splitting of text into nested chunks enabling multi-granularity retrieval from summary to detail
- **locality_sensitive_hashing** (d2): Hashing scheme preserving similarity relationships; used in approximate_nearest_neighbor for fast vector_database queries
- **overlapping_chunks** (d2): Chunking strategy where adjacent chunks share boundary tokens to prevent information loss at chunk_boundaries
- **context_fidelity** (d3): The accuracy with which context content reflects ground truth; low fidelity leads to hallucinated reasoning from corrupted context
- **associative_memory** (d3): Recall triggered by related concepts; attention mechanism is a form of content-addressable associative memory enabling retrieval by similarity.

## CONSUMERS (what needs this)
`retrieval_augmented_generation`, `system_message`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*