# understand-bloaters

**CALL NUMBER:** `refactoring_catalog_and_code_smells.bloaters`
**DEFINITION:** Code smells indicating structures that have grown excessively large and difficult to work with.

Invoke this skill to understand `bloaters` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `refactoring_catalog_and_code_smells`
- **data_clump** (d1): A group of variables appearing together in multiple locations, indicating a missing class or abstraction.
- **large_class** (d1): A class containing too many responsibilities, fields, or lines of code indicating violation of single responsibility.
- **long_method** (d1): A method that has grown too large, typically exceeding dozens of lines, making it hard to understand and maintain.
- **long_parameter_list** (d1): A function or method requiring excessive parameters, suggesting missing abstraction or parameter object.
- **primitive_obsession** (d1): Using primitive types where small objects would provide better semantics, type safety, and expressiveness.

## CONSUMERS (what needs this)
`brain_overload`

---
*Projected from the `refactoring catalog and code smells` KB (183 concepts / 128 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*