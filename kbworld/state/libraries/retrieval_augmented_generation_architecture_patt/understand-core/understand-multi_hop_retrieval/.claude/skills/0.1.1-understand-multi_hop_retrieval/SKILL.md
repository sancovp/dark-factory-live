---
name: 0.1.1-understand-multi_hop_retrieval
description: [0.1.1] Retrieval strategy that executes multiple sequential retrieval steps, where each step uses the output or conte
---

# understand-multi_hop_retrieval

**CALL NUMBER:** `?.multi_hop_retrieval : retrieval_augmented_generation_architecture_patt(1)`
**DEFINITION:** Retrieval strategy that executes multiple sequential retrieval steps, where each step uses the output or context of prior steps to formulate improved queries, enabling the system to gather information spanning multiple关系的 hops through a knowledge graph or document corpus.

Invoke this skill to understand `multi_hop_retrieval` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `retrieval_augmented_generation_architecture_patt`
- **query_decomposition_rag** (d1): RAG pattern that breaks complex queries into sub-questions, retrieves for each, and synthesizes answers from distributed contexts

## CONSUMERS (what needs this)
`graph_rag`, `iterative_retrieval`, `multi_hop_rrieval`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
