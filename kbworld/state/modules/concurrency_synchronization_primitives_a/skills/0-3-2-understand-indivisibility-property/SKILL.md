---
name: 0.3.2-understand-indivisibility_property
description: "[0.3.2] The fundamental property that a relaxed atomic operation executes as a single indivisible step from the perspe"
---

# understand-indivisibility_property

**CALL NUMBER:** `deep_c11_memory_model.indivisibility_property`
**DEFINITION:** The fundamental property that a relaxed atomic operation executes as a single indivisible step from the perspective of all threads; the operation either completes fully or not at all without observable intermediate states.

Invoke this skill to understand `indivisibility_property` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_c11_memory_model`
- **intermediate_state_invisibility** (d1): The guarantee that no thread can observe a partially completed relaxed atomic operation; all threads observe either the state before or after the operation, never during its execution.
- **load_indivisibility** (d1): A relaxed atomic load returns exactly one value from the modification order of the target variable; no torn read of a partial value encoded in fewer bits than the atomic word is possible.
- **no_partial_observation** (d1): The constraint that observers of a relaxed atomic operation cannot see byte-level or word-level fragments of the operation in flight; only complete before or after states are visible.
- **no_tearing_guarantee** (d1): The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.
- **read_modify_write_indivisibility** (d1): The indivisibility of compound read-modify-write operations under relaxed ordering; fetch_add fetch_sub and similar operations complete atomically without observable intermediate states.
- **store_indivisibility** (d1): A relaxed atomic store writes the complete value as one indivisible step; no intermediate write of a partial value encoded in fewer bits than the atomic word is observable by any thread.

## CONSUMERS (what needs this)
`atomic_alignment_prerequisite_enables_indivisibility_guarantee`, `indivisibility_guarantee`, `indivisibility_guarantee_scope_limited_to_target_variable`, `memory_order_relaxed`, `memory_order_relaxed_atomicity_guarantee`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
