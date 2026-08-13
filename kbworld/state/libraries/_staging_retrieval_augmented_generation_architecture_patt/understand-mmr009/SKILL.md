# understand-mmr009

**CALL NUMBER:** `deep_retrieval_augmented_.mmr009`
**DEFINITION:** Multi-modal index: index structure supporting heterogeneous chunk types — text vectors, image features, table embeddings — with metadata routing for modality-aware retrieval.

Invoke this skill to understand `mmr009` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_retrieval_augmented_`
- **mmr001** (d1): Modality type: classification of data representation forms a retrieval system handles — text, image, table, code, audio, video, or structured data.
- **mmr002** (d1): Multi-modal embedding model: neural network architecture that projects content from different modalities into a shared vector space enabling cross-modal similarity search.
- **mmr005** (d2): Non-text chunk processor: component that parses, extracts, and encodes non-text content from documents — handling image pixels, table cells, code syntax, or audio waveforms into retrievable representations.
- **mmr012** (d2): Cross-modal similarity metric: distance or similarity measure applicable across modality boundaries — enabling comparison of text query vectors against image embeddings, for example.

## CONSUMERS (what needs this)
`mmr015`, `mmr026`, `mmr027`, `naive_rag`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*