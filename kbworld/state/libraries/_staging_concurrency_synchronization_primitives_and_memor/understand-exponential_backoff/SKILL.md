# understand-exponential_backoff

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.exponential_backoff : deep_spinlock(9)`
**DEFINITION:** Contention management strategy backing off exponentially after failed lock acquisition; reduces bus traffic and collision; common in spinlock and CAS-based algorithm implementations.

Invoke this skill to understand `exponential_backoff` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **thundering_herd** (d1): Pattern where many threads wake simultaneously from a blocking operation but only one can proceed; wasteful of resources; often avoided with wake-one semantics or phased awakening.

### from `deep_spinlock`
- **backoff_iteration** (d1): Zero-based counter tracking how many consecutive failed lock acquisition attempts have occurred since last success.
- **backoff_multiplier** (d1): Scaling factor (commonly 2.0) that multiplies the current delay on each failed acquisition attempt to produce the next delay interval.
- **base_delay** (d1): Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point of the exponential schedule.
- **current_delay** (d1): The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_multiplier raised to the iteration count, then capped by delay_ceiling.
- **delay_ceiling** (d1): Upper bound cap on the computed delay; prevents unbounded growth of wait times when contention persists across many iterations.
- **jitter** (d1): Randomized variance introduced into the computed delay to decorrelate competing threads and mitigate thundering-herd synchronization on lock release.
- **decorrelated_jitter** (d2): Jitter strategy where each thread computes delay = random.uniform(min_delay, previous_delay * 3); history-dependent decorrelation reduces coordinated retry waves.
- **equal_jitter** (d2): Jitter strategy computing delay = base_delay / 2 + random.uniform(0, base_delay / 2); ensures wait never falls below half the nominal delay.
- **full_jitter** (d2): Jitter strategy selecting a uniform random value in the range [0, current_delay]; maximizes desynchronization at the cost of potentially very short waits.

## CONSUMERS (what needs this)
`spinlock`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*