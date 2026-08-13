# understand-constraint

**CALL NUMBER:** `deep_type_inference.constraint : type_systems_for_working_programmers(7)`
**DEFINITION:** An atomic equational condition of the form type_A = type_B produced during constraint_generation, awaiting resolution by unification.

Invoke this skill to understand `constraint` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_type_inference`
- **unification** (d1): The algorithm that, given two monotypes, computes a substitution that makes them syntactically identical, or reports a type_error if impossible.
- **most_general_unifier** (d2): Most general substitution that satisfies a set of type constraints; unique up to renaming of variables.
- **occurs_check** (d2): The guard inside unification that rejects a substitution {α ↦ t} when α occurs free inside t, preventing the construction of infinite recursive types.
- **substitution** (d3): A total function from type_variable to monotype; a mapping recording how each type_variable was solved during constraint_solving.
- **constraint_solving** (d3): The phase that processes the generated constraints via unification, producing the principal substitution.
- **pruning** (d4): The substitution-composition step that replaces a type_variable with its expanded form after unification, eliminating aliasing to type_variables.
- **principal_pair** (d4): Pair consisting of a type scheme and its originating type environment; the full inference result.
- **free_type_variables** (d5): Set of type variables occurring in a type that are not quantified; relevant to generalization.
- **constraint_generation** (d7): The phase that walks the syntax tree of an expression under a type_environment, producing a set of constraints paired with an accumulating type_environment for subterms.
- **type_environment** (d7): A finite mapping from term_variable names to type_schemes, providing the typing assumptions available at a given point during constraint_generation.

### from `type_systems_for_working_programmers`
- **type_error** (d2): Violation of type constraints detected by the type system (static or runtime).
- **type_variable** (d4): Placeholder symbol ranging over types, awaiting instantiation (alpha in Hindley-Milner).
- **hindley_milner** (d5): Classical type inference algorithm supporting parametric polymorphism and let-generalization.
- **predicative_polymorphism** (d6): Polymorphism restricted to monomorphic types inside quantifiers (ML/Hindley-Milner).
- **type_inference** (d6): Compiler or runtime deducing types from context without explicit annotation.
- **principal_type** (d7): Most general type capturing all valid typings for an expression.
- **type_annotation** (d7): Explicit syntactic marker associating a name or expression with a type (e.g. x: int).

## CONSUMERS (what needs this)
`constraint_generation`, `ct_constraint`, `type_annotation`, `type_variable`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*