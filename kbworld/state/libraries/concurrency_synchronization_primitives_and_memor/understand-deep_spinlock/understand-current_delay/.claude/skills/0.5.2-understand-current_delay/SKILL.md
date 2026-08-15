---
name: 0.5.2-understand-current_delay
description: [0.5.2] The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_mult
---

# understand-current_delay

**CALL NUMBER:** `deep_spinlock.current_delay : deep_exponential_backoff(4)`
**DEFINITION:** The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_multiplier raised to the iteration count, then capped by delay_ceiling.

Invoke this skill to understand `current_delay` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **djt_min_delay** (d2): Lower bound of the uniform sampling range in decorrelated jitter; typically derived from base_delay and serves as the floor below which no wait interval may fall, ensuring at least a minimal pause before retry.
- **djt_bounding_range** (d3): The closed interval [min_delay, previous_delay times decorrelation_factor] from which the uniform random sample is drawn to compute the next current_delay; bounds the worst-case wait while allowing history-dependent growth.
- **djt_random_uniform_sample** (d4): The uniform random draw within the bounding range that produces the new current_delay value; the randomness decorrelates this thread's retry timing from concurrent threads.
- **djt_wave_attenuation** (d5): The emergent property that decorrelated jitter reduces the probability of simultaneous retries among competing threads; achieved through per-thread history-dependent ranges that diverge over time.

### from `deep_spinlock`
- **backoff_multiplier** (d1): Scaling factor (commonly 2.0) that multiplies the current delay on each failed acquisition attempt to produce the next delay interval.
- **base_delay** (d1): Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point of the exponential schedule.
- **delay_ceiling** (d1): Upper bound cap on the computed delay; prevents unbounded growth of wait times when contention persists across many iterations.

## CONSUMERS (what needs this)
`exponential_backoff`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (211 concepts / 207 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
