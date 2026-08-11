---
name: 0.3.5-understand-couplers
description: [0.3.5] Code smells indicating excessive or inappropriate dependencies between classes and modules.
---

# understand-couplers

**CALL NUMBER:** `refactoring_catalog_and_code_smells.couplers`
**DEFINITION:** Code smells indicating excessive or inappropriate dependencies between classes and modules.

Invoke this skill to understand `couplers` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `refactoring_catalog_and_code_smells`
- **feature_envy** (d1): A method more interested in data of other classes than its own, suggesting the method belongs elsewhere.
- **inappropriate_intimacy** (d1): Two classes with excessive coupling, accessing each other's private details in inappropriate ways.
- **message_chain** (d1): A series of chained method calls like a.getB().getC().getD(), creating tight coupling across the chain.
- **middle_man** (d1): A class delegating almost all work to another class, indicating unnecessary indirection or missing abstraction.

## CONSUMERS (what needs this)
`cyclic_dependency`

---
*Projected from the `refactoring catalog and code smells` KB (183 concepts / 128 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
