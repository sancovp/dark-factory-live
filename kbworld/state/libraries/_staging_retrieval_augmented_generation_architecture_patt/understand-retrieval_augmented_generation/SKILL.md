# understand-retrieval_augmented_generation

**CALL NUMBER:** `retrieval_augmented_generation_architecture_patt.retrieval_augmented_generation : deep_retrieval_augmented_(20)`
**DEFINITION:** Paradigm that augments language model generation with information retrieved from external knowledge sources to improve factual accuracy and reduce hallucination

Invoke this skill to understand `retrieval_augmented_generation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **multi_hop_retrieval** (d2): Retrieval strategy that executes multiple sequential retrieval steps, where each step uses the output or context of prior steps to formulate improved queries, enabling the system to gather information spanning multiple关系的 hops through a knowledge graph or document corpus.

### from `deep_retrieval_augmented_`
- **mmr014** (d2): Modality confidence scorer: scoring function estimating retrieval quality per modality, enabling fallback decisions when a modality's results are unreliable.
- **mmr018** (d2): Scene graph extractor: parsing visual content into structured entity-relationship graphs capturing objects, attributes, and spatial relationships for graph-based retrieval.
- **mmr001** (d2): Modality type: classification of data representation forms a retrieval system handles — text, image, table, code, audio, video, or structured data.
- **mmr003** (d2): Cross-modal retrieval: searching for content in one modality using a query from a different modality, such as retrieving images from a text query or code from a table context.
- **mmr004** (d2): Modal fusion strategy: mechanism for combining or harmonizing representations from multiple modalities — early fusion (embedding-level concatenation), late fusion (score-level aggregation), or intermediate fusion (attention-based cross-modal interaction).
- **mmr027** (d2): Multi-modal context builder: constructing the generation-augmenting context by assembling retrieved chunks of mixed types, handling format conversion and ordering for downstream generation.
- **mmr005** (d2): Non-text chunk processor: component that parses, extracts, and encodes non-text content from documents — handling image pixels, table cells, code syntax, or audio waveforms into retrievable representations.
- **mmr009** (d2): Multi-modal index: index structure supporting heterogeneous chunk types — text vectors, image features, table embeddings — with metadata routing for modality-aware retrieval.
- **mmr021** (d2): Multi-modal query router: routing layer classifying query type and directing retrieval toward appropriate modality-specific or cross-modal retrieval paths.
- **mmr013** (d2): Multi-modal reranker: post-retrieval component that reorders mixed-modality candidates using cross-attention between query and all retrieved content types.
- **mmr010** (d3): Modality-specific retriever: specialized retrieval component tuned to a particular modality's retrieval patterns, scoring functions, and similarity measures.
- **mmr017** (d3): Image description encoder: vision model producing text-aligned representations of images — captions, scene graphs, or dense captions — enabling image content in text-based retrieval.
- **mmr002** (d3): Multi-modal embedding model: neural network architecture that projects content from different modalities into a shared vector space enabling cross-modal similarity search.
- **mmr012** (d3): Cross-modal similarity metric: distance or similarity measure applicable across modality boundaries — enabling comparison of text query vectors against image embeddings, for example.
- **mmr006** (d3): Table extraction: parsing structured tabular data from documents or PDFs into machine-readable format with row/column headers preserved for retrieval and reasoning.
- **mmr016** (d3): Table-to-text generator: component converting retrieved tabular data into natural language summaries or explanations for injection into the generation prompt.
- **mmr023** (d3): Code semantic embedder: embedding code snippets capturing functional semantics, API usage patterns, and documentation context for semantic code retrieval.
- **mmr011** (d3): Heterogeneous retrieval engine: unified retrieval layer that queries across mixed content types, resolving modality mismatches and ranking results from diverse sources.
- **mmr007** (d4): Image/figure extraction: isolating visual elements from documents — charts, diagrams, photographs — for separate encoding and retrieval alongside text.
- **mmr008** (d4): Code chunk handler: processing code snippets with language-aware parsing to capture syntax, imports, function signatures, and docstrings as retrieval units.

### from `retrieval_augmented_generation_architecture_patt`
- **agentic_rag** (d1): RAG system where an LLM agent iteratively decides retrieval actions, queries, and when to stop based on intermediate reasoning steps
- **conversational_rag** (d1): Multi-turn RAG that maintains conversation history, resolves coreferences, and retrieves contextually relevant information across dialogue turns
- **corrective_rag** (d1): RAG architecture with explicit error detection: low-quality retrieval triggers fallback to web search or re-retrieval strategies
- **graph_rag** (d1): RAG variant that retrieves from knowledge graphs or builds graphs over document chunks to capture entity relationships and community structure
- **multi_modal_rag** (d1): RAG system that retrieves and augments generation with images, tables, code, or other non-text modalities alongside text
- **naive_rag** (d1): Basic RAG architecture: query embedding, vector similarity search, context injection, generation — simple pipeline without optimization refinements
- **query_decomposition_rag** (d1): RAG pattern that breaks complex queries into sub-questions, retrieves for each, and synthesizes answers from distributed contexts
- **router_based_rag** (d1): RAG with a routing layer that directs queries to specialized retrievers, vector stores, or generation modes based on query classification
- **self_rag** (d1): Self-reflective RAG where the generator evaluates retrieved passages and its own generations for relevance, utility, and hallucination using special tokens
- **speculative_rag** (d1): RAG pattern where a smaller model drafts candidates that a larger model then verifies against retrieved context
- **memory_augmented_rag** (d2): RAG with persistent or working memory storing prior retrieval results, conversation state, or learned retrieval patterns
- **query_understanding** (d2): Pre-retrieval analysis parsing query intent, entities, temporal constraints, and required information types
- **fallback_retrieval** (d2): Secondary retrieval strategy activated when primary retrieval yields insufficient results or low confidence
- **retrieval_confidence** (d2): Scored certainty measure of retrieved result relevance enabling downstream thresholding or fallback decisions
- **advanced_rag** (d2): RAG pipeline with preprocessing (query expansion, rewriting) and postprocessing (reranking, relevance filtering) stages surrounding core retrieval
- **query_type_routing** (d2): Classifying query into factual, conversational, analytical, or procedural types to select appropriate retrieval strategy
- **iterative_retrieval** (d2): Multi-pass retrieval where each round uses previous retrieval results to inform and refine the next query
- **speculative_decoding** (d2): Generation acceleration: draft tokens with small model, verify with large model conditioned on retrieved context
- **modular_rag** (d3): RAG architecture decomposed into interchangeable components: retrievers, rerankers, routers, generators, and memory modules assembled per task

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*