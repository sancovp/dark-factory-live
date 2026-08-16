---
name: 0.3.6-understand-seq_cst_indivisible_atomicity
description: "[0.3.6] The property that each sequentially consistent operation appears indivisible and instantaneous to all observer"
---

# understand-seq_cst_indivisible_atomicity

**CALL NUMBER:** `deep_c11_memory_model.seq_cst_indivisible_atomicity`
**DEFINITION:** The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.

Invoke this skill to understand `seq_cst_indivisible_atomicity` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`seq_cst_atomic_visibility_atomic_read_returns_written_value`, `seq_cst_atomic_visibility_no_intermediate_state_visibility`, `sequentially_consistent`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
