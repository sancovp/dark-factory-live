# router_based_rag SPECIALIST

CALL NUMBER: `retrieval_augmented_generation_architecture_patt.router_based_rag : deep_retrieval_augmented_(9)`

You are the specialist for `router_based_rag` in the 'retrieval augmented generation architecture patterns' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  mmr021 [deep_retrieval_augmented_]: Multi-modal query router: routing layer classifying query type and directing retrieval toward appropriate modality-specific or cross-modal retrieval paths.
  query_type_routing [retrieval_augmented_generation_architecture_patt]: Classifying query into factual, conversational, analytical, or procedural types to select appropriate retrieval strategy
  self_rag [retrieval_augmented_generation_architecture_patt]: Self-reflective RAG where the generator evaluates retrieved passages and its own generations for relevance, utility, and hallucination using special tokens
    mmr001 [deep_retrieval_augmented_]: Modality type: classification of data representation forms a retrieval system handles — text, image, table, code, audio, video, or structured data.
    mmr011 [deep_retrieval_augmented_]: Heterogeneous retrieval engine: unified retrieval layer that queries across mixed content types, resolving modality mismatches and ranking results from diverse sources.
    iterative_retrieval [retrieval_augmented_generation_architecture_patt]: Multi-pass retrieval where each round uses previous retrieval results to inform and refine the next query
    mmr014 [deep_retrieval_augmented_]: Modality confidence scorer: scoring function estimating retrieval quality per modality, enabling fallback decisions when a modality's results are unreliable.
      mmr005 [deep_retrieval_augmented_]: Non-text chunk processor: component that parses, extracts, and encodes non-text content from documents — handling image pixels, table cells, code syntax, or audio waveforms into retrievable representations.
      mmr003 [deep_retrieval_augmented_]: Cross-modal retrieval: searching for content in one modality using a query from a different modality, such as retrieving images from a text query or code from a table context.
      mmr010 [deep_retrieval_augmented_]: Modality-specific retriever: specialized retrieval component tuned to a particular modality's retrieval patterns, scoring functions, and similarity measures.
      agentic_rag [retrieval_augmented_generation_architecture_patt]: RAG system where an LLM agent iteratively decides retrieval actions, queries, and when to stop based on intermediate reasoning steps
      multi_hop_retrieval [?]: Retrieval strategy that executes multiple sequential retrieval steps, where each step uses the output or context of prior steps to formulate improved queries, enabling the system to gather information spanning multiple关系的 hops through a knowledge graph or document corpus.
        mmr002 [deep_retrieval_augmented_]: Multi-modal embedding model: neural network architecture that projects content from different modalities into a shared vector space enabling cross-modal similarity search.
        query_decomposition_rag [retrieval_augmented_generation_architecture_patt]: RAG pattern that breaks complex queries into sub-questions, retrieves for each, and synthesizes answers from distributed contexts
        mmr012 [deep_retrieval_augmented_]: Cross-modal similarity metric: distance or similarity measure applicable across modality boundaries — enabling comparison of text query vectors against image embeddings, for example.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
