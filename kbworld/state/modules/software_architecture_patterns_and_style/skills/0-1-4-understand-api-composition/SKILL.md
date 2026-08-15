---
name: 0.1.4-understand-api_composition
description: "[0.1.4] A pattern where a facade or aggregation layer combines data from multiple backend services or APIs into a sing"
---

# understand-api_composition

**CALL NUMBER:** `?.api_composition : deep_microservices_archit(16), software_architecture_patterns_and_styles(7)`
**DEFINITION:** A pattern where a facade or aggregation layer combines data from multiple backend services or APIs into a single unified response, enabling clients to retrieve consolidated results without managing multiple round-trips or service contracts.

Invoke this skill to understand `api_composition` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_microservices_archit`
- **gateway_routing__integration** (d3): Integration with load_balancing to distribute requests across multiple instances of a backend service.
- **gateway_routing_backend_service** (d3): A microservice or backend resource that receives forwarded requests from the gateway.
- **gateway_routing_circuit_breaker_integration** (d3): Integration with circuit_breaker logic to prevent routing to failing backend services.
- **gateway_routing_fallback_route** (d3): A predefined route or behavior triggered when primary routing fails or no route matches.
- **gateway_routing_response_aggregation** (d3): The combination of responses from multiple backend services into a single client response.
- **gateway_routing_reverse_proxy** (d3): The mechanism that forwards matched requests to backend services and returns responses to clients.
- **gateway_routing_route** (d3): A defined mapping between incoming request criteria and a target backend service endpoint.
- **gateway_routing_service_discovery_integration** (d3): Integration with service_discovery to dynamically resolve backend service network locations.
- **gateway_routing_header_transformation** (d4): The addition, removal, or modification of HTTP headers during request forwarding.
- **gateway_routing_path_rewrite** (d4): A transformation that modifies the request path before forwarding to the backend service.
- **gateway_routing_route_definition** (d4): The declarative or imperative specification of a route including matching criteria and target service.
- **gateway_routing_request_matcher** (d5): A component that evaluates incoming requests against route matching criteria.
- **gateway_routing_route_priority** (d5): The ordering rule that determines which route takes precedence when multiple routes match.
- **gateway_routing_header_condition** (d6): A matching rule based on request or response header values for routing decisions.
- **gateway_routing_http_method_filter** (d6): A routing constraint based on HTTP method (GET, POST, PUT, DELETE) for route matching.
- **gateway_routing_path_pattern** (d6): A URL path template or pattern used to match incoming request paths for routing decisions.

### from `software_architecture_patterns_and_styles`
- **api_gateway** (d1): A server entry point that routes requests to backend services, handling cross-cutting concerns like authentication, rate_limiting, and protocol_translation.
- **gateway_routing** (d2): A pattern where an API_gateway routes requests to appropriate backend services based on request characteristics (URL path, headers) without the client knowing service locations.
- **rate_limiting** (d2): A traffic_management technique that controls how many requests a client can make in a given time period, protecting services from overload and abuse.
- **load_balancing** (d4): A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
- **service_discovery** (d4): The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
- **horizontal_scaling** (d5): Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
- **auto_scaling** (d6): Automatically adjusting the number of compute instances based on demand metrics (CPU, request_count, queue_depth), improving resource efficiency.

## CONSUMERS (what needs this)
`aggregator_pattern`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
