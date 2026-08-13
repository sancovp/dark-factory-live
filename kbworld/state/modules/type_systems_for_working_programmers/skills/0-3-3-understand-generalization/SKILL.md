---
name: 0.3.3-understand-generalization
description: "[0.3.3] Operation that abstracts free type variables into quantified variables, forming a type scheme."
---

# understand-generalization

**CALL NUMBER:** `deep_type_inference.generalization`
**DEFINITION:** Operation that abstracts free type variables into quantified variables, forming a type scheme.

Invoke this skill to understand `generalization` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_type_inference`
- **free_type_variables** (d1): Set of type variables occurring in a type that are not quantified; relevant to generalization.
- **monotype** (d1): Type with no quantified variables; ground type or type variable instantiation result.
- **type_scheme** (d1): Type with universally quantified variables; pairs a monotype with a set of type variables in scope.
- **polytype** (d2): Synonym for type scheme; a type with forall-quantified variables enabling polymorphism.

## CONSUMERS (what needs this)
`algorithm_w`, `let_polymorphism`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
