---
name: 0.5.3-understand-inter_thread_happens_before
description: [0.5.3] The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connecti
---

# understand-inter_thread_happens_before

**CALL NUMBER:** `deep_happens_before_relat.inter_thread_happens_before`
**DEFINITION:** The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.

Invoke this skill to understand `inter_thread_happens_before` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **happens_before_order** (d1): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

## CONSUMERS (what needs this)
`hb_interrupt_visibility`, `hb_reads_from`, `program_order`, `sw_inter_thread_happens_before`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
