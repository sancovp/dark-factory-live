# relaxed_store_buffering_vs_acquire_visibility_guarantee

[deep_c11_memory_model · d1] The buffering contrast where relaxed stores may remain indefinitely in store buffers and become visible to other threads in an order different from program order, while acquire semantics guarantees that all prior writes by the releasing thread become visible to the acquiring thread before the acquire completes.
