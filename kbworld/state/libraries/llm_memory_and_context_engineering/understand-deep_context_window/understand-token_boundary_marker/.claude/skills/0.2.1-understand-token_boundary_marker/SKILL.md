---
name: 0.2.1-understand-token_boundary_marker
description: [0.2.1] The positional delimiter marking the transition from input context to output generation; tokens before this ma
---

# understand-token_boundary_marker

**CALL NUMBER:** `deep_context_window.token_boundary_marker`
**DEFINITION:** The positional delimiter marking the transition from input context to output generation; tokens before this marker are provided context, tokens after are to be generated.

Invoke this skill to understand `token_boundary_marker` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_context_window`
- **sequence_position** (d1): The ordinal index of a token within the full context sequence; constrained to be less than or equal to maximum_position.

## CONSUMERS (what needs this)
`context_length`, `input_token_budget`, `output_token_limit`, `tokenization_scheme`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
