# understand-hb_acquire_semantics

**CALL NUMBER:** `deep_happens_before_relat.hb_acquire_semantics`
**DEFINITION:** A memory ordering guarantee where all subsequent memory operations become visible only after the acquire operation; paired with release to establish synchronization.

Invoke this skill to understand `hb_acquire_semantics` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **hb_lock_acquire** (d1): Acquiring a synchronization lock, which carries acquire semantics for all operations following the acquisition.

## CONSUMERS (what needs this)
`hb_acquire_fence`, `hb_lock_acquire`, `hb_synchronizes_with`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*