# understand-hb_transitive_closure

**CALL NUMBER:** `deep_happens_before_relat.hb_transitive_closure`
**DEFINITION:** The transitive property of happens-before: if A happens-before B and B happens-before C, then A happens-before C.

Invoke this skill to understand `hb_transitive_closure` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`hb_carries_dependency`, `hb_program_order`, `hb_synchronizes_with`, `hb_transitivity`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*