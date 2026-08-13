---
name: 0.4.1-understand-current_delay
description: "[0.4.1] The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_mult"
---

# understand-current_delay

**CALL NUMBER:** `deep_spinlock.current_delay`
**DEFINITION:** The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_multiplier raised to the iteration count, then capped by delay_ceiling.

Invoke this skill to understand `current_delay` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_spinlock`
- **backoff_multiplier** (d1): Scaling factor (commonly 2.0) that multiplies the current delay on each failed acquisition attempt to produce the next delay interval.
- **base_delay** (d1): Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point of the exponential schedule.
- **delay_ceiling** (d1): Upper bound cap on the computed delay; prevents unbounded growth of wait times when contention persists across many iterations.

## CONSUMERS (what needs this)
`exponential_backoff`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
