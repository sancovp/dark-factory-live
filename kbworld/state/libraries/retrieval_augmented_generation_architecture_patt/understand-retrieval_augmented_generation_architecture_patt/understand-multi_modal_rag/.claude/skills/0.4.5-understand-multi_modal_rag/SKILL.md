---
name: 0.4.5-understand-multi_modal_rag
description: [0.4.5] RAG system that retrieves and augments generation with images, tables, code, or other non-text modalities alon
---

# understand-multi_modal_rag

**CALL NUMBER:** `retrieval_augmented_generation_architecture_patt.multi_modal_rag : deep_retrieval_augmented_(14)`
**DEFINITION:** RAG system that retrieves and augments generation with images, tables, code, or other non-text modalities alongside text

Invoke this skill to understand `multi_modal_rag` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_retrieval_augmented_`
- **mmr001** (d1): Modality type: classification of data representation forms a retrieval system handles — text, image, table, code, audio, video, or structured data.
- **mmr003** (d1): Cross-modal retrieval: searching for content in one modality using a query from a different modality, such as retrieving images from a text query or code from a table context.
- **mmr004** (d1): Modal fusion strategy: mechanism for combining or harmonizing representations from multiple modalities — early fusion (embedding-level concatenation), late fusion (score-level aggregation), or intermediate fusion (attention-based cross-modal interaction).
- **mmr027** (d1): Multi-modal context builder: constructing the generation-augmenting context by assembling retrieved chunks of mixed types, handling format conversion and ordering for downstream generation.
- **mmr005** (d2): Non-text chunk processor: component that parses, extracts, and encodes non-text content from documents — handling image pixels, table cells, code syntax, or audio waveforms into retrievable representations.
- **mmr002** (d2): Multi-modal embedding model: neural network architecture that projects content from different modalities into a shared vector space enabling cross-modal similarity search.
- **mmr012** (d2): Cross-modal similarity metric: distance or similarity measure applicable across modality boundaries — enabling comparison of text query vectors against image embeddings, for example.
- **mmr006** (d2): Table extraction: parsing structured tabular data from documents or PDFs into machine-readable format with row/column headers preserved for retrieval and reasoning.
- **mmr009** (d2): Multi-modal index: index structure supporting heterogeneous chunk types — text vectors, image features, table embeddings — with metadata routing for modality-aware retrieval.
- **mmr016** (d2): Table-to-text generator: component converting retrieved tabular data into natural language summaries or explanations for injection into the generation prompt.
- **mmr017** (d2): Image description encoder: vision model producing text-aligned representations of images — captions, scene graphs, or dense captions — enabling image content in text-based retrieval.
- **mmr023** (d2): Code semantic embedder: embedding code snippets capturing functional semantics, API usage patterns, and documentation context for semantic code retrieval.
- **mmr007** (d3): Image/figure extraction: isolating visual elements from documents — charts, diagrams, photographs — for separate encoding and retrieval alongside text.
- **mmr008** (d3): Code chunk handler: processing code snippets with language-aware parsing to capture syntax, imports, function signatures, and docstrings as retrieval units.

## CONSUMERS (what needs this)
`retrieval_augmented_generation`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
