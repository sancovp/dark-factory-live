---
name: 0.6.3-understand-isi_no_in_flight_state
description: [0.6.3] The guaranteed absence of any transient value during operation execution that could be sampled by a concurrent
---

# understand-isi_no_in_flight_state

**CALL NUMBER:** `deep_indivisibility_prope.isi_no_in_flight_state`
**DEFINITION:** The guaranteed absence of any transient value during operation execution that could be sampled by a concurrent thread; the in-flight state is logically invisible.

Invoke this skill to understand `isi_no_in_flight_state` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_indivisibility_prope`
- **isi_load_visibility_rule** (d1): For a relaxed atomic load, the read returns exactly one value from the modification order; no torn read of a partial encoding is observable.
- **isi_rmw_visibility_rule** (d1): For a relaxed read-modify-write operation, observers see either the complete state before the modification or the complete state after modification; the read-modify-write executes atomically without observable intermediate stages.
- **isi_store_visibility_rule** (d1): For a relaxed atomic store, any reading thread observes either the complete value that existed before the store or the complete value after the store; torn writes are impossible.

## CONSUMERS (what needs this)
`isi_operation_completeness`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
