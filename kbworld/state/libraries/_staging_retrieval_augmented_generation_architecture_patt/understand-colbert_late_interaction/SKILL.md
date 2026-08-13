# understand-colbert_late_interaction

**CALL NUMBER:** `deep_dense_retrieval.colbert_late_interaction`
**DEFINITION:** Core architectural principle deferring interaction between query and document token representations until scoring time, enabling efficient per-token similarity computation without full cross-encoding of query-document pairs.

Invoke this skill to understand `colbert_late_interaction` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_dense_retrieval`
- **colbert_maxsim_operator** (d1): Maximum similarity operator that for each query token finds the highest-scoring document token via cosine similarity, then aggregates across query tokens to produce document relevance score.
- **colbert_reductional_scoring** (d1): Late scoring mechanism reducing query-document interaction to token-level maximum similarities then aggregating, contrasted with full cross-encoder joint encoding.
- **colbert_token_aggregation** (d1): Aggregation function combining per-token similarity scores (typically sum or mean over query tokens) to produce final document relevance score in late interaction framework.
- **colbert_token_embedding** (d2): Dense contextualized vector representation produced per token by an encoder model, preserving token identity and positional context for late interaction scoring.
- **colbert_cross_encoder_comparison** (d2): Comparison metric distinguishing ColBERT from cross-encoder reranking: ColBERT scores via token-level max-sim aggregation whereas cross-encoder produces single joint representation per pair.
- **colbert_document_encoder** (d3): Encoder producing per-token document embeddings from document passages, typically run offline and indexed for fast retrieval against query embeddings.
- **colbert_query_encoder** (d3): Encoder producing per-token query embeddings from input query tokens, enabling efficient single-pass encoding with late interaction against document tokens.
- **colbert_representation_rank** (d4): Rank dimension of per-token embeddings determining expressiveness of token-level similarity computation in late interaction framework.

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*