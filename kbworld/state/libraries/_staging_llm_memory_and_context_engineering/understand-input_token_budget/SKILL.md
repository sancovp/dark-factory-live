# understand-input_token_budget

**CALL NUMBER:** `deep_context_window.input_token_budget`
**DEFINITION:** The portion of context_length reserved and available for prompt tokens, retrieved context, and system instructions before generation begins.

Invoke this skill to understand `input_token_budget` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_context_window`
- **output_token_limit** (d1): The portion of context_length reserved for generated tokens; equals context_length minus input_token_budget minus overhead tokens.
- **token_boundary_marker** (d1): The positional delimiter marking the transition from input context to output generation; tokens before this marker are provided context, tokens after are to be generated.
- **token_headroom** (d1): The arithmetic difference between current position or token count and context_boundary; the remaining room before overflow_threshold is reached.
- **sequence_position** (d2): The ordinal index of a token within the full context sequence; constrained to be less than or equal to maximum_position.
- **overflow_threshold** (d2): The position or token count at which the model behavior shifts from normal processing to truncation or error; often slightly below context_boundary.
- **context_resize_event** (d3): The runtime mechanism or policy invoked when context_length must accommodate inputs exceeding current capacity; involves reallocation or overflow handling.

## CONSUMERS (what needs this)
`context_length`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*