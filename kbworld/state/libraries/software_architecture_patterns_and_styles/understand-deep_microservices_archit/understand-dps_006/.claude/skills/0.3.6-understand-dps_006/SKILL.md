---
name: 0.3.6-understand-dps_006
description: [0.3.6] data_duplication is the consequence of database_per_service where the same logical entity may be materialized 
---

# understand-dps_006

**CALL NUMBER:** `deep_microservices_archit.dps_006 : software_architecture_patterns_and_styles(15), deep_event_driven_archite(9)`
**DEFINITION:** data_duplication is the consequence of database_per_service where the same logical entity may be materialized in multiple service databases, kept synchronized through application-level events.

Invoke this skill to understand `dps_006` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **distributed_transaction** (d3): A transaction that spans multiple independent services or database_per_service instances, requiring coordination to maintain atomicity across nodes where each participant may reside in a different process or machine.

### from `deep_event_driven_archite`
- **pubsub_broker** (d3): The intermediary component that receives messages from publishers and forwards them to subscribers based on topic subscriptions; may also perform filtering.
- **pubsub_topic** (d3): A named channel or subject through which messages are routed from publishers to interested subscribers; the publisher has no knowledge of subscriber identities or count.
- **pubsub_message** (d3): The payload broadcast by a publisher on a topic; in pub/sub it is typically ephemeral and not persisted beyond active subscriber consumption.
- **pubsub_dead_letter** (d4): A destination for messages that cannot be successfully delivered to any subscriber, capturing failures for later inspection or replay.
- **pubsub_subscription** (d4): An active registration linking a subscriber to a topic; may be durable (surviving subscriber disconnection) or transient (active only while subscriber is connected).
- **pubsub_topic_namespace** (d4): A hierarchical or scoped naming scheme for topics (e.g., orders.new, orders.cancelled) that enables subscribers to express interest at varying levels of granularity.
- **pubsub_content_filter** (d4): A predicate or attribute-based rule applied at the broker or subscriber side to select a subset of messages on a topic for delivery.
- **pubsub_message_schema** (d4): A structured format (JSON, Avro, Protobuf) defining the shape of messages on a topic, enabling subscribers to deserialize and interpret published events.
- **pubsub_subscriber** (d5): An entity that expresses interest in one or more topics and receives messages published to those topics; receives only messages matching its subscriptions.

### from `deep_microservices_archit`
- **dps_007** (d1): api_composition is the pattern where a client or gateway aggregates data from multiple service databases by querying each service's API and combining results, compensating for the lack of cross-service SQL joins.
- **dps_014** (d1): eventual_consistency_model is the consistency guarantee that results from database_per_service: writes are immediately durable in one service's database, and other services receive updates asynchronously via event_streaming or message_queue.
- **gateway_routing__integration** (d4): Integration with load_balancing to distribute requests across multiple instances of a backend service.
- **gateway_routing_backend_service** (d4): A microservice or backend resource that receives forwarded requests from the gateway.
- **gateway_routing_circuit_breaker_integration** (d4): Integration with circuit_breaker logic to prevent routing to failing backend services.
- **gateway_routing_fallback_route** (d4): A predefined route or behavior triggered when primary routing fails or no route matches.
- **gateway_routing_response_aggregation** (d4): The combination of responses from multiple backend services into a single client response.
- **gateway_routing_reverse_proxy** (d4): The mechanism that forwards matched requests to backend services and returns responses to clients.
- **gateway_routing_route** (d4): A defined mapping between incoming request criteria and a target backend service endpoint.
- **gateway_routing_service_discovery_integration** (d4): Integration with service_discovery to dynamically resolve backend service network locations.
- **gateway_routing_header_transformation** (d5): The addition, removal, or modification of HTTP headers during request forwarding.
- **gateway_routing_path_rewrite** (d5): A transformation that modifies the request path before forwarding to the backend service.
- **gateway_routing_route_definition** (d5): The declarative or imperative specification of a route including matching criteria and target service.
- **gateway_routing_request_matcher** (d6): A component that evaluates incoming requests against route matching criteria.
- **gateway_routing_route_priority** (d6): The ordering rule that determines which route takes precedence when multiple routes match.
- **gateway_routing_header_condition** (d7): A matching rule based on request or response header values for routing decisions.
- **gateway_routing_http_method_filter** (d7): A routing constraint based on HTTP method (GET, POST, PUT, DELETE) for route matching.
- **gateway_routing_path_pattern** (d7): A URL path template or pattern used to match incoming request paths for routing decisions.

### from `software_architecture_patterns_and_styles`
- **api_gateway** (d2): A server entry point that routes requests to backend services, handling cross-cutting concerns like authentication, rate_limiting, and protocol_translation.
- **event_streaming** (d2): A data handling approach where events are captured in order as an immutable log (stream), allowing multiple consumers to read independently (e.g., Kafka, Pulsar).
- **message_queue** (d2): A communication mechanism where messages are placed in a queue by producers and consumed asynchronously by consumers, decoupling sender and receiver in time and space.
- **publish_subscribe_pattern** (d2): A messaging pattern where publishers send messages to a topic without knowing subscribers, and subscribers receive messages published to topics they are interested in.
- **saga_pattern** (d2): A pattern for managing distributed transactions across microservices using a sequence of local transactions with compensating actions for rollback, replacing distributed transactions.
- **gateway_routing** (d3): A pattern where an API_gateway routes requests to appropriate backend services based on request characteristics (URL path, headers) without the client knowing service locations.
- **rate_limiting** (d3): A traffic_management technique that controls how many requests a client can make in a given time period, protecting services from overload and abuse.
- **choreography_pattern** (d3): A distributed coordination pattern where services exchange events without a central orchestrator; each service knows what to do based on received events.
- **orchestration_pattern** (d3): A distributed coordination pattern where a central coordinator (orchestrator) directs the flow of operations across services, contrasting with choreography.
- **event_driven_architecture** (d4): A software design pattern where the flow of the program is determined by events (user actions, sensor outputs, messages) and the propagation of events through the system.
- **service_oriented_architecture** (d4): An architectural pattern where application components provide services to other components via a communication protocol, typically over a network. SOA emphasizes interoperability and composition of services.
- **load_balancing** (d5): A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
- **service_discovery** (d5): The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
- **horizontal_scaling** (d6): Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
- **auto_scaling** (d7): Automatically adjusting the number of compute instances based on demand metrics (CPU, request_count, queue_depth), improving resource efficiency.

## CONSUMERS (what needs this)
`dps_001`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
