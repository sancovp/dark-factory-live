---
name: 0.4.2-understand-context_length
description: [0.4.2] Total number of tokens (input + output) an LLM supports; the hard ceiling on how much text can be loaded into 
---

# understand-context_length

**CALL NUMBER:** `llm_memory_and_context_engineering.context_length : deep_context_window(13)`
**DEFINITION:** Total number of tokens (input + output) an LLM supports; the hard ceiling on how much text can be loaded into context_window at once

Invoke this skill to understand `context_length` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_context_window`
- **context_boundary** (d1): The hard edge position within context where context_overflow triggers if exceeded; exactly context_length minus one for the output region.
- **context_resize_event** (d1): The runtime mechanism or policy invoked when context_length must accommodate inputs exceeding current capacity; involves reallocation or overflow handling.
- **context_scaling_factor** (d1): The multiplier relating raw context_length to effective_context; models with improved attention patterns achieve factors closer to one.
- **input_token_budget** (d1): The portion of context_length reserved and available for prompt tokens, retrieved context, and system instructions before generation begins.
- **max_model_tokens** (d1): The absolute token ceiling of the model architecture; synonymous with context_length when no additional constraints apply.
- **maximum_position** (d1): The highest valid integer position index representable by the position_embedding scheme within context_length; equal to max_model_tokens minus one for zero-indexed sequences.
- **output_token_limit** (d1): The portion of context_length reserved for generated tokens; equals context_length minus input_token_budget minus overhead tokens.
- **overflow_threshold** (d1): The position or token count at which the model behavior shifts from normal processing to truncation or error; often slightly below context_boundary.
- **token_boundary_marker** (d1): The positional delimiter marking the transition from input context to output generation; tokens before this marker are provided context, tokens after are to be generated.
- **context_capacity_ratio** (d2): The ratio of tokens actively processed to total available context_length; quantifies context_utilization as used_capacity divided by max_model_tokens.
- **token_headroom** (d2): The arithmetic difference between current position or token count and context_boundary; the remaining room before overflow_threshold is reached.
- **position_index** (d2): Ordinal integer from zero to context_window_boundary representing each token's location in the sequence; each index must be encodable by the position_embedding scheme in use
- **sequence_position** (d2): The ordinal index of a token within the full context sequence; constrained to be less than or equal to maximum_position.

### from `llm_memory_and_context_engineering`
- **context_padding** (d1): Appending empty tokens to extend context to alignment boundaries; inefficient but sometimes necessary for batch processing
- **token_accounting** (d1): Tracking token usage across context_building operations to ensure neither context_window nor max_tokens limits are exceeded
- **effective_context** (d2): Portion of context_window the model actually leverages for any given generation; often less than the full window due to attention patterns

## CONSUMERS (what needs this)
`c_util_007`, `c_util_008`, `context_window`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
