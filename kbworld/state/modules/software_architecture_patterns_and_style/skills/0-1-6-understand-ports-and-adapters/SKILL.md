---
name: 0.1.6-understand-ports_and_adapters
description: "[0.1.6] An architectural pattern that separates the core business logic from external concerns by defining ports (inte"
---

# understand-ports_and_adapters

**CALL NUMBER:** `?.ports_and_adapters : software_architecture_patterns_and_styles(2)`
**DEFINITION:** An architectural pattern that separates the core business logic from external concerns by defining ports (interfaces) for inputs and outputs, with adapters implementing those ports to connect to frameworks, databases, or external systems.

Invoke this skill to understand `ports_and_adapters` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `software_architecture_patterns_and_styles`
- **hexagonal_architecture** (d1): An architectural pattern (ports_and_adapters) that structures the application with a core business logic at the center, surrounded by ports for input and output adapters, keeping the core independent of external concerns.
- **dependency_inversion_principle** (d2): A SOLID principle stating that high-level modules should not depend on low-level modules; both should depend on abstractions (interfaces), not concrete implementations.

## CONSUMERS (what needs this)
`hexagonal_architecture`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
