# spinlock

CALL NUMBER: `concurrency_synchronization_primitives_and_memor.spinlock`

Lock implementation that spins in a tight loop waiting for acquisition; efficient when contention is brief but wasteful if held long; often implemented with atomic instructions.
