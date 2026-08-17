# understand-hb_release_semantics

**CALL NUMBER:** `deep_happens_before_relat.hb_release_semantics`
**DEFINITION:** A memory ordering guarantee where all prior memory operations become visible before the release operation; paired with acquire to establish synchronization.

Invoke this skill to understand `hb_release_semantics` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **hb_lock_release** (d1): Releasing a synchronization lock, which carries release semantics for all operations preceding the release.

## CONSUMERS (what needs this)
`hb_lock_release`, `hb_release_fence`, `hb_synchronizes_with`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*