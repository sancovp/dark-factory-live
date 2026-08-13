# mcs_lock

[concurrency_synchronization_primitives_and_memor · d1] Queued lock where each waiting thread spins on a locally-owned node linked into a queue; cache-friendly with only O(1) bus traffic per lock acquisition; named after Mellor-Crummey and Scott.
