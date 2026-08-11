---
name: 0.3.6-understand-brain_overload
description: [0.3.6] Cognitive complexity where a class or method requires too much context to understand, straining working memory
---

# understand-brain_overload

**CALL NUMBER:** `refactoring_catalog_and_code_smells.brain_overload`
**DEFINITION:** Cognitive complexity where a class or method requires too much context to understand, straining working memory.

Invoke this skill to understand `brain_overload` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `refactoring_catalog_and_code_smells`
- **bloaters** (d1): Code smells indicating structures that have grown excessively large and difficult to work with.
- **oop_abusers** (d1): Code smells indicating incorrect or incomplete use of object-oriented constructs and patterns.
- **data_clump** (d2): A group of variables appearing together in multiple locations, indicating a missing class or abstraction.
- **large_class** (d2): A class containing too many responsibilities, fields, or lines of code indicating violation of single responsibility.
- **long_method** (d2): A method that has grown too large, typically exceeding dozens of lines, making it hard to understand and maintain.
- **long_parameter_list** (d2): A function or method requiring excessive parameters, suggesting missing abstraction or parameter object.
- **primitive_obsession** (d2): Using primitive types where small objects would provide better semantics, type safety, and expressiveness.
- **refused_bequest** (d2): A subclass using only some inherited methods, suggesting inheritance hierarchy is wrong or composition preferred.
- **switch_statement_smell** (d2): Repeated switch statements across code paths, suggesting need for polymorphism or lookup table.
- **temporary_field** (d2): Fields in a class populated only under certain conditions, indicating missing abstraction or state pattern.

## CONSUMERS (what needs this)
`decompose_conditional`, `replace_magic_number`, `replace_nested_conditionals_with_guard_clauses`

---
*Projected from the `refactoring catalog and code smells` KB (183 concepts / 128 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
