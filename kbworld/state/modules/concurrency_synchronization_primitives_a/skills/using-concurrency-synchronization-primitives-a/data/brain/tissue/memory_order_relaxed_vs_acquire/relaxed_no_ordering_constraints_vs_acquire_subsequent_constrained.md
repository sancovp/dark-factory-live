# relaxed_no_ordering_constraints_vs_acquire_subsequent_constrained

[deep_c11_memory_model · d1] The scope contrast where relaxed operations impose zero ordering constraints on any other operations on any memory location, while acquire semantics constrains all subsequent loads and stores in the same thread to remain after the acquire in program order.
