---
name: 0.3.4-understand-mmr003
description: "[0.3.4] Cross-modal retrieval: searching for content in one modality using a query from a different modality, such as "
---

# understand-mmr003

**CALL NUMBER:** `deep_retrieval_augmented_.mmr003`
**DEFINITION:** Cross-modal retrieval: searching for content in one modality using a query from a different modality, such as retrieving images from a text query or code from a table context.

Invoke this skill to understand `mmr003` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_retrieval_augmented_`
- **mmr002** (d1): Multi-modal embedding model: neural network architecture that projects content from different modalities into a shared vector space enabling cross-modal similarity search.
- **mmr012** (d2): Cross-modal similarity metric: distance or similarity measure applicable across modality boundaries — enabling comparison of text query vectors against image embeddings, for example.

## CONSUMERS (what needs this)
`mmr011`, `mmr013`, `mmr022`, `mmr026`, `multi_modal_rag`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
