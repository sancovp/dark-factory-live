---
name: 0.2.5-understand-colbert_maxsim_operator
description: "[0.2.5] Maximum similarity operator that for each query token finds the highest-scoring document token via cosine simi"
---

# understand-colbert_maxsim_operator

**CALL NUMBER:** `deep_dense_retrieval.colbert_maxsim_operator`
**DEFINITION:** Maximum similarity operator that for each query token finds the highest-scoring document token via cosine similarity, then aggregates across query tokens to produce document relevance score.

Invoke this skill to understand `colbert_maxsim_operator` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_dense_retrieval`
- **colbert_token_embedding** (d1): Dense contextualized vector representation produced per token by an encoder model, preserving token identity and positional context for late interaction scoring.
- **colbert_document_encoder** (d2): Encoder producing per-token document embeddings from document passages, typically run offline and indexed for fast retrieval against query embeddings.
- **colbert_query_encoder** (d2): Encoder producing per-token query embeddings from input query tokens, enabling efficient single-pass encoding with late interaction against document tokens.
- **colbert_representation_rank** (d3): Rank dimension of per-token embeddings determining expressiveness of token-level similarity computation in late interaction framework.

## CONSUMERS (what needs this)
`colbert_late_interaction`, `colbert_token_aggregation`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
