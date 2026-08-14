# understand-maximum_position

**CALL NUMBER:** `deep_context_window.maximum_position`
**DEFINITION:** The highest valid integer position index representable by the position_embedding scheme within context_length; equal to max_model_tokens minus one for zero-indexed sequences.

Invoke this skill to understand `maximum_position` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_context_window`
- **position_index** (d1): Ordinal integer from zero to context_window_boundary representing each token's location in the sequence; each index must be encodable by the position_embedding scheme in use
- **sequence_position** (d1): The ordinal index of a token within the full context sequence; constrained to be less than or equal to maximum_position.

## CONSUMERS (what needs this)
`context_length`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*