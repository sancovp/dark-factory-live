---
name: 0.3.4-understand-pt02
description: [0.3.4] type_inference: the algorithmic process of deriving types for expressions by propagating constraints from know
---

# understand-pt02

**CALL NUMBER:** `deep_type_inference.pt02`
**DEFINITION:** type_inference: the algorithmic process of deriving types for expressions by propagating constraints from known types through the syntax tree

Invoke this skill to understand `pt02` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_type_inference`
- **pt03** (d1): type_variable: a placeholder symbol in a type that remains unresolved until unification binds it to a concrete or more general type
- **pt06** (d1): type_constraint: an equation of the form T1 = T2 between two types that must hold for a valid typing
- **pt08** (d1): generalization: the operation that lifts free type variables into a type scheme, forming a polytype from a monotype
- **pt09** (d1): instantiation: replacing quantified variables in a type scheme with fresh type variables, yielding a less-general type
- **pt04** (d2): unification: the algorithm that finds the most general substitution making two types equal, central to constraint solving in inference
- **pt07** (d2): type_scheme: a type paired with quantified type variables, enabling polymorphism by separating generic from monomorphic occurrences
- **pt13** (d2): free_type_variables: type variables occurring in an expression that are not bound by a surrounding lambda and thus subject to generalization
- **pt05** (d3): substitution: a mapping from type variables to types that, when applied, resolves all variables in a type expression

## CONSUMERS (what needs this)
`pt01`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
