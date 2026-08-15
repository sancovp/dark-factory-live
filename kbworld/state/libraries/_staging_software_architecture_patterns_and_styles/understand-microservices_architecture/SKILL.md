# understand-microservices_architecture

**CALL NUMBER:** `software_architecture_patterns_and_styles.microservices_architecture : deep_microservices_archit(16), deep_event_driven_archite(9)`
**DEFINITION:** An architectural style that structures an application as a collection of small, autonomous, loosely-coupled services organized around business capabilities, each deployable independently and communicating via lightweight protocols.

Invoke this skill to understand `microservices_architecture` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **distributed_transaction** (d2): A transaction that spans multiple independent services or database_per_service instances, requiring coordination to maintain atomicity across nodes where each participant may reside in a different process or machine.

### from `deep_event_driven_archite`
- **pubsub_broker** (d5): The intermediary component that receives messages from publishers and forwards them to subscribers based on topic subscriptions; may also perform filtering.
- **pubsub_topic** (d5): A named channel or subject through which messages are routed from publishers to interested subscribers; the publisher has no knowledge of subscriber identities or count.
- **pubsub_message** (d5): The payload broadcast by a publisher on a topic; in pub/sub it is typically ephemeral and not persisted beyond active subscriber consumption.
- **pubsub_dead_letter** (d6): A destination for messages that cannot be successfully delivered to any subscriber, capturing failures for later inspection or replay.
- **pubsub_subscription** (d6): An active registration linking a subscriber to a topic; may be durable (surviving subscriber disconnection) or transient (active only while subscriber is connected).
- **pubsub_topic_namespace** (d6): A hierarchical or scoped naming scheme for topics (e.g., orders.new, orders.cancelled) that enables subscribers to express interest at varying levels of granularity.
- **pubsub_content_filter** (d6): A predicate or attribute-based rule applied at the broker or subscriber side to select a subset of messages on a topic for delivery.
- **pubsub_message_schema** (d6): A structured format (JSON, Avro, Protobuf) defining the shape of messages on a topic, enabling subscribers to deserialize and interpret published events.
- **pubsub_subscriber** (d7): An entity that expresses interest in one or more topics and receives messages published to those topics; receives only messages matching its subscriptions.

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
- **database_per_service** (d1): A data management pattern in microservices where each service owns and manages its own database schema or instance, enforcing loose coupling.
- **saga_pattern** (d1): A pattern for managing distributed transactions across microservices using a sequence of local transactions with compensating actions for rollback, replacing distributed transactions.
- **service_discovery** (d1): The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
- **service_mesh** (d1): A dedicated infrastructure layer that handles service_to_service communication, providing observability, traffic_management, and security without embedding this logic in application code (e.g., Istio, Linkerd).
- **shared_database** (d1): An anti_pattern in microservices where multiple services share the same database, creating tight coupling and hindering independent deployment.
- **gateway_routing** (d2): A pattern where an API_gateway routes requests to appropriate backend services based on request characteristics (URL path, headers) without the client knowing service locations.
- **rate_limiting** (d2): A traffic_management technique that controls how many requests a client can make in a given time period, protecting services from overload and abuse.
- **choreography_pattern** (d2): A distributed coordination pattern where services exchange events without a central orchestrator; each service knows what to do based on received events.
- **orchestration_pattern** (d2): A distributed coordination pattern where a central coordinator (orchestrator) directs the flow of operations across services, contrasting with choreography.
- **load_balancing** (d2): A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
- **sidecar_pattern** (d2): A deployment pattern where a helper container (sidecar) is attached to a main application container to extend or add functionality without modifying the application.
- **anti_pattern** (d2): A commonly used pattern that appears beneficial but is actually counterproductive; architectural anti_patterns include big_ball_of_mud, golden_hammer, and spaghetti_code.
- **event_driven_architecture** (d3): A software design pattern where the flow of the program is determined by events (user actions, sensor outputs, messages) and the propagation of events through the system.
- **service_oriented_architecture** (d3): An architectural pattern where application components provide services to other components via a communication protocol, typically over a network. SOA emphasizes interoperability and composition of services.
- **horizontal_scaling** (d3): Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
- **ambassador_service** (d3): A helper service that offloads client-side network responsibilities (retry, circuit_breaker, monitoring) from the application into a sidecar container.
- **event_streaming** (d4): A data handling approach where events are captured in order as an immutable log (stream), allowing multiple consumers to read independently (e.g., Kafka, Pulsar).
- **message_queue** (d4): A communication mechanism where messages are placed in a queue by producers and consumed asynchronously by consumers, decoupling sender and receiver in time and space.
- **publish_subscribe_pattern** (d4): A messaging pattern where publishers send messages to a topic without knowing subscribers, and subscribers receive messages published to topics they are interested in.
- **auto_scaling** (d4): Automatically adjusting the number of compute instances based on demand metrics (CPU, request_count, queue_depth), improving resource efficiency.

## CONSUMERS (what needs this)
`bounded_context`, `contract_testing`, `strangler_fig_pattern`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*