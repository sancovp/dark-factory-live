# in_context_learning SPECIALIST

CALL NUMBER: `llm_memory_and_context_engineering.in_context_learning : deep_long_term_memory(14), deep_context_window(13)`

You are the specialist for `in_context_learning` in the 'llm memory and context engineering' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  attention_mechanism [llm_memory_and_context_engineering]: The core operation allowing each token to attend to all others; scaled dot-product attention is the standard. Memory and context are both outputs of attention computation.
  context_window [llm_memory_and_context_engineering]: The finite token sequence an LLM can process in a single forward pass; defines the maximum input + output capacity bounded by architecture or inference config
  few_shot_learning [llm_memory_and_context_engineering]: Providing 2-5 examples in context to guide task performance; example selection and ordering affect success significantly.
    attention_saturation [llm_memory_and_context_engineering]: Condition where attention weights become uniform across long context; signals reduced context_utilization and effective_context shrinkage
    attention_sinks [llm_memory_and_context_engineering]: Special tokens that accumulate disproportionate attention mass, enabling efficient long-context modeling without explicit positional encoding
    attention_weighting [llm_memory_and_context_engineering]: Distribution of attention scores across context tokens; reveals what the model considers relevant to current generation
    cross_attention [llm_memory_and_context_engineering]: Attention mechanism where queries attend to a separate context (e.g., retrieved documents); enables retrieval_augmented_generation
    hard_attention [llm_memory_and_context_engineering]: Attention focusing on single positions; non-differentiable but efficient; approximated by soft attention in practice
    kv_cache [llm_memory_and_context_engineering]: The key-value tensors cached during transformer self-attention to avoid recomputing activations for previously-seen tokens
    self_attention [llm_memory_and_context_engineering]: The mechanism by which transformer models relate each token position to all other positions; the quadratic bottleneck in context_length scaling
    soft_attention [llm_memory_and_context_engineering]: Attention producing weighted averages over all positions; differentiable but computationally expensive at scale
    sparse_attention [llm_memory_and_context_engineering]: Attention patterns that compute fewer than n² pairwise interactions, reducing memory_efficient_attention cost at the cost of expressiveness
    context_length [llm_memory_and_context_engineering]: Total number of tokens (input + output) an LLM supports; the hard ceiling on how much text can be loaded into context_window at once
    context_overflow [llm_memory_and_context_engineering]: The failure state where total input exceeds context_window, causing silent truncation or errors depending on the client library
    context_utilization [llm_memory_and_context_engineering]: How effectively the model uses all available context tokens; metrics include attention entropy, retrieval accuracy at various positions, task performance variation with position.
    effective_context [llm_memory_and_context_engineering]: Portion of context_window the model actually leverages for any given generation; often less than the full window due to attention patterns
    flash_attention [llm_memory_and_context_engineering]: A memory-efficient attention algorithm using tiling and recomputation to avoid materializing the full n×n attention matrix in HBM
    position_embedding [llm_memory_and_context_engineering]: Encoding that injects positional information into token representations since attention is permutation-invariant. Choices: sinusoidal, RoPE, ALiBi. Affects how context scales.
    ring_attention [llm_memory_and_context_engineering]: Distributed sliding_window_attention across multiple devices with communication-avoiding algorithms for very long sequences
    sliding_window [llm_memory_and_context_engineering]: Fixed-size contiguous subset of recent tokens kept in working_memory as new tokens arrive and old ones are evicted
    truncation_strategy [llm_memory_and_context_engineering]: Policy for removing old context when context_overflow occurs; options include FIFO, importance-weighted, and semantic summarization
    working_memory [llm_memory_and_context_engineering]: The transient token budget allocated for active reasoning within a single model call; scratch space for chain_of_thought and intermediate results
    prompt_engineering [llm_memory_and_context_engineering]: Crafting input text to elicit desired outputs; includes instruction design, example selection, formatting, and context structuring.
      context_caching [llm_memory_and_context_engineering]: Storing computed key-value pairs from prior forward passes to avoid recomputation on repeated or overlapping context prefixes
      prefix_caching [llm_memory_and_context_engineering]: Caching the KV tensors for shared prefixes (system prompt, few-shot examples) so they aren't recomputed per request; reduces latency and compute for repeated contexts.
      context_boundary [deep_context_window]: The hard edge position within context where context_overflow triggers if exceeded; exactly context_length minus one for the output region.
      context_padding [llm_memory_and_context_engineering]: Appending empty tokens to extend context to alignment boundaries; inefficient but sometimes necessary for batch processing
      context_resize_event [deep_context_window]: The runtime mechanism or policy invoked when context_length must accommodate inputs exceeding current capacity; involves reallocation or overflow handling.
      context_scaling_factor [deep_context_window]: The multiplier relating raw context_length to effective_context; models with improved attention patterns achieve factors closer to one.
      input_token_budget [deep_context_window]: The portion of context_length reserved and available for prompt tokens, retrieved context, and system instructions before generation begins.
      max_model_tokens [deep_context_window]: The absolute token ceiling of the model architecture; synonymous with context_length when no additional constraints apply.
      maximum_position [deep_context_window]: The highest valid integer position index representable by the position_embedding scheme within context_length; equal to max_model_tokens minus one for zero-indexed sequences.
      output_token_limit [deep_context_window]: The portion of context_length reserved for generated tokens; equals context_length minus input_token_budget minus overhead tokens.
      overflow_threshold [deep_context_window]: The position or token count at which the model behavior shifts from normal processing to truncation or error; often slightly below context_boundary.
      token_accounting [llm_memory_and_context_engineering]: Tracking token usage across context_building operations to ensure neither context_window nor max_tokens limits are exceeded
      token_boundary_marker [deep_context_window]: The positional delimiter marking the transition from input context to output generation; tokens before this marker are provided context, tokens after are to be generated.
      backward_recall [llm_memory_and_context_engineering]: Retrieval of past context tokens; constrained by context_window for working_memory and retrieval_mechanism for long_term_memory
      context_horizon [llm_memory_and_context_engineering]: Farthest retrievable or presentable token distance from current position; the effective reach of memory_access
      memory_window [llm_memory_and_context_engineering]: The subset of episodic_memory available for retrieval at any time; analogous to context_window but for long_term_storage

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
