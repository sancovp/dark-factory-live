# relaxed_no_synchronizes_with_vs_acquire_synchronizes_with

[deep_c11_memory_model · d1] The synchronization contrast where relaxed atomic operations do not participate in the synchronizes-with relation and establish no cross-thread ordering, while acquire operations on a matching release create a synchronizes-with relationship establishing inter-thread happens-before.
