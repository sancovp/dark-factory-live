---
name: 0.3.5-understand-memory_order_relaxed_coherence_per_location
description: [0.3.5] The property that each atomic variable maintains its own independent coherence order but this order is not coo
---

# understand-memory_order_relaxed_coherence_per_location

**CALL NUMBER:** `deep_c11_memory_model.memory_order_relaxed_coherence_per_location`
**DEFINITION:** The property that each atomic variable maintains its own independent coherence order but this order is not coordinated with coherence orders of other variables; operations on separate variables are totally unordered with respect to each other.

Invoke this skill to understand `memory_order_relaxed_coherence_per_location` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_c11_memory_model`
- **relaxed_mod_order_no_cross_variable_constraint** (d1): Modification orders of distinct atomic variables have no defined ordering relationship; operations on different variables may be observed in different orders by different threads, per memory_order_relaxed_coherence_per_location.
- **relaxed_mod_order_per_variable** (d1): Each atomic variable maintains its own independent modification order; the modification order for atomic x has no defined relationship with the modification order for atomic y under relaxed semantics.

## CONSUMERS (what needs this)
`memory_order_relaxed`, `memory_order_relaxed_atomicity_guarantee`, `relaxed_coherence_per_location_vs_acquire_global_observation`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
