# relaxed_no_happens_before_edge_vs_acquire_hb_edge

[deep_c11_memory_model · d2] The ordering contrast where relaxed operations never establish a happens-before edge with operations on other threads regardless of visibility timing, while acquire semantics combined with release on another thread creates a transitive happens-before edge connecting the release writer to the acquire reader.
