---
name: 0.1.3-understand-plugin_architecture
description: "[0.1.3] An architectural style where a minimal core system exposes extension points that allow modules (plugins) to be"
---

# understand-plugin_architecture

**CALL NUMBER:** `?.plugin_architecture : software_architecture_patterns_and_styles(1)`
**DEFINITION:** An architectural style where a minimal core system exposes extension points that allow modules (plugins) to be loaded dynamically at runtime, enabling feature extensibility without modifying the core, as employed by microkernel_architecture.

Invoke this skill to understand `plugin_architecture` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `software_architecture_patterns_and_styles`
- **microkernel_architecture** (d1): An architecture with a minimal core (kernel) providing basic OS services, with extended functionality provided by modular plugins or servers. In software, the core handles essential operations while plugins handle specialized features.

## CONSUMERS (what needs this)
`component_based_architecture`, `microkernel_architecture`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
