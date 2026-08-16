---
name: 0.5.3-understand-happens_before_order
description: "[0.5.3] A transitive, irreflexive partial order over operations in a memory model that defines which operations must a"
---

# understand-happens_before_order

**CALL NUMBER:** `deep_happens_before_relat.happens_before_order`
**DEFINITION:** A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

Invoke this skill to understand `happens_before_order` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`hb_causality_order`, `hb_synchronization_order`, `inter_thread_happens_before`, `synchronizes_with_ordering_effect`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
