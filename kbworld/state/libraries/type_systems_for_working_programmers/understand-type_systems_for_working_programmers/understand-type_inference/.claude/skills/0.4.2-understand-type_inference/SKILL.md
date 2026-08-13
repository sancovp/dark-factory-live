---
name: 0.4.2-understand-type_inference
description: [0.4.2] Compiler or runtime deducing types from context without explicit annotation.
---

# understand-type_inference

**CALL NUMBER:** `type_systems_for_working_programmers.type_inference : deep_type_inference(11)`
**DEFINITION:** Compiler or runtime deducing types from context without explicit annotation.

Invoke this skill to understand `type_inference` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_type_inference`
- **constraint_generation** (d1): The phase that walks the syntax tree of an expression under a type_environment, producing a set of constraints paired with an accumulating type_environment for subterms.
- **constraint_solving** (d1): The phase that processes the generated constraints via unification, producing the principal substitution.
- **principal_pair** (d1): Pair consisting of a type scheme and its originating type environment; the full inference result.
- **type_environment** (d1): A finite mapping from term_variable names to type_schemes, providing the typing assumptions available at a given point during constraint_generation.
- **constraint** (d2): An atomic equational condition of the form type_A = type_B produced during constraint_generation, awaiting resolution by unification.
- **substitution** (d2): A total function from type_variable to monotype; a mapping recording how each type_variable was solved during constraint_solving.
- **unification** (d2): The algorithm that, given two monotypes, computes a substitution that makes them syntactically identical, or reports a type_error if impossible.
- **pruning** (d3): The substitution-composition step that replaces a type_variable with its expanded form after unification, eliminating aliasing to type_variables.
- **most_general_unifier** (d3): Most general substitution that satisfies a set of type constraints; unique up to renaming of variables.
- **occurs_check** (d3): The guard inside unification that rejects a substitution {α ↦ t} when α occurs free inside t, preventing the construction of infinite recursive types.
- **free_type_variables** (d4): Set of type variables occurring in a type that are not quantified; relevant to generalization.

### from `type_systems_for_working_programmers`
- **principal_type** (d1): Most general type capturing all valid typings for an expression.
- **type_annotation** (d1): Explicit syntactic marker associating a name or expression with a type (e.g. x: int).
- **type_variable** (d3): Placeholder symbol ranging over types, awaiting instantiation (alpha in Hindley-Milner).
- **type_error** (d3): Violation of type constraints detected by the type system (static or runtime).
- **hindley_milner** (d4): Classical type inference algorithm supporting parametric polymorphism and let-generalization.
- **predicative_polymorphism** (d5): Polymorphism restricted to monomorphic types inside quantifiers (ML/Hindley-Milner).

## CONSUMERS (what needs this)
`algorithm_w`, `hindley_milner`, `recursive_type`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
