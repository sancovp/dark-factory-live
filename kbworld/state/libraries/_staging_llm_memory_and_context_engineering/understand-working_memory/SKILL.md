# understand-working_memory

**CALL NUMBER:** `llm_memory_and_context_engineering.working_memory : deep_context_window(13)`
**DEFINITION:** The transient token budget allocated for active reasoning within a single model call; scratch space for chain_of_thought and intermediate results

Invoke this skill to understand `working_memory` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_context_window`
- **context_boundary** (d3): The hard edge position within context where context_overflow triggers if exceeded; exactly context_length minus one for the output region.
- **context_resize_event** (d3): The runtime mechanism or policy invoked when context_length must accommodate inputs exceeding current capacity; involves reallocation or overflow handling.
- **context_scaling_factor** (d3): The multiplier relating raw context_length to effective_context; models with improved attention patterns achieve factors closer to one.
- **input_token_budget** (d3): The portion of context_length reserved and available for prompt tokens, retrieved context, and system instructions before generation begins.
- **max_model_tokens** (d3): The absolute token ceiling of the model architecture; synonymous with context_length when no additional constraints apply.
- **maximum_position** (d3): The highest valid integer position index representable by the position_embedding scheme within context_length; equal to max_model_tokens minus one for zero-indexed sequences.
- **output_token_limit** (d3): The portion of context_length reserved for generated tokens; equals context_length minus input_token_budget minus overhead tokens.
- **overflow_threshold** (d3): The position or token count at which the model behavior shifts from normal processing to truncation or error; often slightly below context_boundary.
- **token_boundary_marker** (d3): The positional delimiter marking the transition from input context to output generation; tokens before this marker are provided context, tokens after are to be generated.
- **context_capacity_ratio** (d4): The ratio of tokens actively processed to total available context_length; quantifies context_utilization as used_capacity divided by max_model_tokens.
- **token_headroom** (d4): The arithmetic difference between current position or token count and context_boundary; the remaining room before overflow_threshold is reached.
- **position_index** (d4): Ordinal integer from zero to context_window_boundary representing each token's location in the sequence; each index must be encodable by the position_embedding scheme in use
- **sequence_position** (d4): The ordinal index of a token within the full context sequence; constrained to be less than or equal to maximum_position.

### from `llm_memory_and_context_engineering`
- **attention_mechanism** (d1): The core operation allowing each token to attend to all others; scaled dot-product attention is the standard. Memory and context are both outputs of attention computation.
- **chain_of_thought** (d1): Producing intermediate reasoning steps before final answer; when demonstrated in context, subsequent reasoning follows the pattern. A form of contextual procedural memory.
- **context_window** (d1): The finite token sequence an LLM can process in a single forward pass; defines the maximum input + output capacity bounded by architecture or inference config
- **memory_efficiency** (d1): Ratio of useful information retained per unit of memory storage or context_token budget
- **memory_hierarchy** (d1): The layered structure of LLM memory: immediate context (working), retrieved context (RAG), fine-tuned weights (parametric), external stores (vector DB). Each layer has different latency/capacity tradeoffs.
- **memory_window** (d1): The subset of episodic_memory available for retrieval at any time; analogous to context_window but for long_term_storage
- **scratchpad** (d1): Explicit intermediate reasoning space written by the model itself; a form of ephemeral working_memory externalized to tokens
- **sliding_window** (d1): Fixed-size contiguous subset of recent tokens kept in working_memory as new tokens arrive and old ones are evicted
- **attention_saturation** (d2): Condition where attention weights become uniform across long context; signals reduced context_utilization and effective_context shrinkage
- **attention_sinks** (d2): Special tokens that accumulate disproportionate attention mass, enabling efficient long-context modeling without explicit positional encoding
- **attention_weighting** (d2): Distribution of attention scores across context tokens; reveals what the model considers relevant to current generation
- **cross_attention** (d2): Attention mechanism where queries attend to a separate context (e.g., retrieved documents); enables retrieval_augmented_generation
- **hard_attention** (d2): Attention focusing on single positions; non-differentiable but efficient; approximated by soft attention in practice
- **kv_cache** (d2): The key-value tensors cached during transformer self-attention to avoid recomputing activations for previously-seen tokens
- **self_attention** (d2): The mechanism by which transformer models relate each token position to all other positions; the quadratic bottleneck in context_length scaling
- **soft_attention** (d2): Attention producing weighted averages over all positions; differentiable but computationally expensive at scale
- **sparse_attention** (d2): Attention patterns that compute fewer than n² pairwise interactions, reducing memory_efficient_attention cost at the cost of expressiveness
- **causal_tracing** (d2): Technique identifying which context tokens causally influence model outputs; used to understand effective_context and attention patterns
- **context_length** (d2): Total number of tokens (input + output) an LLM supports; the hard ceiling on how much text can be loaded into context_window at once
- **context_overflow** (d2): The failure state where total input exceeds context_window, causing silent truncation or errors depending on the client library
- **context_utilization** (d2): How effectively the model uses all available context tokens; metrics include attention entropy, retrieval accuracy at various positions, task performance variation with position.
- **effective_context** (d2): Portion of context_window the model actually leverages for any given generation; often less than the full window due to attention patterns
- **flash_attention** (d2): A memory-efficient attention algorithm using tiling and recomputation to avoid materializing the full n×n attention matrix in HBM
- **position_embedding** (d2): Encoding that injects positional information into token representations since attention is permutation-invariant. Choices: sinusoidal, RoPE, ALiBi. Affects how context scales.
- **ring_attention** (d2): Distributed sliding_window_attention across multiple devices with communication-avoiding algorithms for very long sequences

## CONSUMERS (what needs this)
`chain_of_thought`, `context_window`, `kv_cache`, `sliding_window`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*