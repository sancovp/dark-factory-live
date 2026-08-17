# relaxed_program_order_preservation_vs_acquire_fence_effect

[deep_c11_memory_model · d2] The barrier contrast where relaxed operations preserve intra-thread program order only for the storing thread's own perspective without cross-thread visibility guarantees, while acquire semantics acts as a memory fence that prevents both the compiler and processor from moving subsequent operations before the acquire point.
