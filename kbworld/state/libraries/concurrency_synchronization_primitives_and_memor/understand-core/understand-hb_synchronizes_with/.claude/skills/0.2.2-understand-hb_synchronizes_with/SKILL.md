---
name: 0.2.2-understand-hb_synchronizes_with
description: [0.2.2] A synchronization operation or primitive that establishes an inter-thread happens-before relationship, ensurin
---

# understand-hb_synchronizes_with

**CALL NUMBER:** `?.hb_synchronizes_with : deep_happens_before_relat(5)`
**DEFINITION:** A synchronization operation or primitive that establishes an inter-thread happens-before relationship, ensuring that all memory effects preceding the synchronization point in one thread become visible to all operations following the corresponding synchronization point in another thread; the fundamental mechanism by which threads coordinate access to shared state, encompassing operations such as th

Invoke this skill to understand `hb_synchronizes_with` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **hb_acquire_semantics** (d1): A memory ordering guarantee where all subsequent memory operations become visible only after the acquire operation; paired with release to establish synchronization.
- **hb_release_semantics** (d1): A memory ordering guarantee where all prior memory operations become visible before the release operation; paired with acquire to establish synchronization.
- **hb_transitive_closure** (d1): The transitive property of happens-before: if A happens-before B and B happens-before C, then A happens-before C.
- **hb_lock_acquire** (d2): Acquiring a synchronization lock, which carries acquire semantics for all operations following the acquisition.
- **hb_lock_release** (d2): Releasing a synchronization lock, which carries release semantics for all operations preceding the release.

## CONSUMERS (what needs this)
`hb_program_order`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
