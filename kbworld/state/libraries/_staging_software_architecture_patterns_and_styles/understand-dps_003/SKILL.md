# understand-dps_003

**CALL NUMBER:** `deep_microservices_archit.dps_003 : software_architecture_patterns_and_styles(4)`
**DEFINITION:** instance_isolation means each service runs its own database server process or cluster, with separate credentials, ports, and storage, preventing any service from accessing another's data store directly.

Invoke this skill to understand `dps_003` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_microservices_archit`
- **dps_010** (d1): connection_pool_per_service means each service manages its own database connection pool, sized independently based on that service's concurrency needs.
- **dps_011** (d1): backup_and_recovery_scope defines that each service backs up and restores only its own database, making recovery operations independent across services.
- **dps_012** (d1): service_catalog_entry is the registration of a service's database connection metadata (host, port, credentials ref) in a service_discovery registry, so authorized services or operators can locate it.

### from `software_architecture_patterns_and_styles`
- **service_discovery** (d2): The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
- **load_balancing** (d3): A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
- **horizontal_scaling** (d4): Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
- **auto_scaling** (d5): Automatically adjusting the number of compute instances based on demand metrics (CPU, request_count, queue_depth), improving resource efficiency.

## CONSUMERS (what needs this)
`dps_001`, `dps_004`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*