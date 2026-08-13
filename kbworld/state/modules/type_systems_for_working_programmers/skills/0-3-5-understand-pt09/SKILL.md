---
name: 0.3.5-understand-pt09
description: "[0.3.5] instantiation: replacing quantified variables in a type scheme with fresh type variables, yielding a less-gene"
---

# understand-pt09

**CALL NUMBER:** `deep_type_inference.pt09`
**DEFINITION:** instantiation: replacing quantified variables in a type scheme with fresh type variables, yielding a less-general type

Invoke this skill to understand `pt09` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_type_inference`
- **pt07** (d1): type_scheme: a type paired with quantified type variables, enabling polymorphism by separating generic from monomorphic occurrences

## CONSUMERS (what needs this)
`pt02`, `pt07`, `pt11`, `pt12`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
