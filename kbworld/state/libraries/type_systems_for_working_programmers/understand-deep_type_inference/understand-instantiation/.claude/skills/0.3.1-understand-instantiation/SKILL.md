---
name: 0.3.1-understand-instantiation
description: [0.3.1] Operation that replaces quantified variables in a type scheme with fresh type variables.
---

# understand-instantiation

**CALL NUMBER:** `deep_type_inference.instantiation : type_systems_for_working_programmers(7)`
**DEFINITION:** Operation that replaces quantified variables in a type scheme with fresh type variables.

Invoke this skill to understand `instantiation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_type_inference`
- **monotype** (d1): Type with no quantified variables; ground type or type variable instantiation result.
- **renaming** (d1): The fresh-variable generation step that replaces a type_variable with a distinct new type_variable during instantiation or when lifting quantifiers, ensuring no capture of free variables.
- **type_scheme** (d1): Type with universally quantified variables; pairs a monotype with a set of type variables in scope.
- **polytype** (d2): Synonym for type scheme; a type with forall-quantified variables enabling polymorphism.
- **constraint** (d2): An atomic equational condition of the form type_A = type_B produced during constraint_generation, awaiting resolution by unification.
- **free_type_variables** (d2): Set of type variables occurring in a type that are not quantified; relevant to generalization.
- **substitution** (d2): A total function from type_variable to monotype; a mapping recording how each type_variable was solved during constraint_solving.
- **unification** (d3): The algorithm that, given two monotypes, computes a substitution that makes them syntactically identical, or reports a type_error if impossible.
- **pruning** (d3): The substitution-composition step that replaces a type_variable with its expanded form after unification, eliminating aliasing to type_variables.
- **most_general_unifier** (d4): Most general substitution that satisfies a set of type constraints; unique up to renaming of variables.
- **occurs_check** (d4): The guard inside unification that rejects a substitution {α ↦ t} when α occurs free inside t, preventing the construction of infinite recursive types.
- **constraint_generation** (d4): The phase that walks the syntax tree of an expression under a type_environment, producing a set of constraints paired with an accumulating type_environment for subterms.
- **constraint_solving** (d4): The phase that processes the generated constraints via unification, producing the principal substitution.
- **principal_pair** (d4): Pair consisting of a type scheme and its originating type environment; the full inference result.
- **type_environment** (d4): A finite mapping from term_variable names to type_schemes, providing the typing assumptions available at a given point during constraint_generation.

### from `type_systems_for_working_programmers`
- **type_variable** (d1): Placeholder symbol ranging over types, awaiting instantiation (alpha in Hindley-Milner).
- **hindley_milner** (d2): Classical type inference algorithm supporting parametric polymorphism and let-generalization.
- **predicative_polymorphism** (d3): Polymorphism restricted to monomorphic types inside quantifiers (ML/Hindley-Milner).
- **type_inference** (d3): Compiler or runtime deducing types from context without explicit annotation.
- **type_error** (d4): Violation of type constraints detected by the type system (static or runtime).
- **principal_type** (d4): Most general type capturing all valid typings for an expression.
- **type_annotation** (d4): Explicit syntactic marker associating a name or expression with a type (e.g. x: int).

## CONSUMERS (what needs this)
`algorithm_w`, `let_polymorphism`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
