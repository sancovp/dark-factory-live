# understand-gateway_routing_request_matcher

**CALL NUMBER:** `deep_microservices_archit.gateway_routing_request_matcher`
**DEFINITION:** A component that evaluates incoming requests against route matching criteria.

Invoke this skill to understand `gateway_routing_request_matcher` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_microservices_archit`
- **gateway_routing_header_condition** (d1): A matching rule based on request or response header values for routing decisions.
- **gateway_routing_http_method_filter** (d1): A routing constraint based on HTTP method (GET, POST, PUT, DELETE) for route matching.
- **gateway_routing_path_pattern** (d1): A URL path template or pattern used to match incoming request paths for routing decisions.

## CONSUMERS (what needs this)
`gateway_routing_route_definition`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*