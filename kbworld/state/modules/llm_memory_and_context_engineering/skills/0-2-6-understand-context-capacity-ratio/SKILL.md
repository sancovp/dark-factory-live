---
name: 0.2.6-understand-context_capacity_ratio
description: "[0.2.6] The ratio of tokens actively processed to total available context_length; quantifies context_utilization as us"
---

# understand-context_capacity_ratio

**CALL NUMBER:** `deep_context_window.context_capacity_ratio : llm_memory_and_context_engineering(1)`
**DEFINITION:** The ratio of tokens actively processed to total available context_length; quantifies context_utilization as used_capacity divided by max_model_tokens.

Invoke this skill to understand `context_capacity_ratio` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `llm_memory_and_context_engineering`
- **effective_context** (d1): Portion of context_window the model actually leverages for any given generation; often less than the full window due to attention patterns

## CONSUMERS (what needs this)
`context_padding`, `token_density`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
