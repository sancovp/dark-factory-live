---
name: 0.3.5-understand-dps_002
description: "[0.3.5] schema_isolation means each service's database exposes only the data and operations relevant to its bounded co"
---

# understand-dps_002

**CALL NUMBER:** `deep_microservices_archit.dps_002`
**DEFINITION:** schema_isolation means each service's database exposes only the data and operations relevant to its bounded context, hiding internal structures from other services.

Invoke this skill to understand `dps_002` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_microservices_archit`
- **dps_005** (d1): schema_ownership declares that a service is the sole authority for defining, migrating, and evolving its database schema; no other service may modify it.
- **dps_009** (d2): migration_orchestration is the process of evolving a service's schema independently, typically done via versioned migration scripts (e.g., Flyway, Liquibase) that each service applies on its own schedule.

## CONSUMERS (what needs this)
`dps_001`, `dps_004`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
