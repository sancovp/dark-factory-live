# understand-dps_001

**CALL NUMBER:** `deep_microservices_archit.dps_001 : software_architecture_patterns_and_styles(15), deep_event_driven_archite(9)`
**DEFINITION:** database_per_service is a data management pattern in microservices where each service owns and manages its own database schema or instance, enforcing loose coupling between services through physical data isolation.

Invoke this skill to understand `dps_001` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

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
- **dps_002** (d1): schema_isolation means each service's database exposes only the data and operations relevant to its bounded context, hiding internal structures from other services.
- **dps_003** (d1): instance_isolation means each service runs its own database server process or cluster, with separate credentials, ports, and storage, preventing any service from accessing another's data store directly.
- **dps_006** (d1): data_duplication is the consequence of database_per_service where the same logical entity may be materialized in multiple service databases, kept synchronized through application-level events.
- **dps_014** (d1): eventual_consistency_model is the consistency guarantee that results from database_per_service: writes are immediately durable in one service's database, and other services receive updates asynchronously via event_streaming or message_queue.
- **dps_015** (d1): shared_nothing_architecture is the architectural property that database_per_service embodies: no shared disk, no shared schema, no shared connection pool across service boundaries.
- **dps_016** (d1): bounded_context_enforcement is the enforcement of domain-driven design bounded contexts through database_per_service, where each context's canonical model is stored only in its own database.
- **dps_005** (d2): schema_ownership declares that a service is the sole authority for defining, migrating, and evolving its database schema; no other service may modify it.
- **dps_010** (d2): connection_pool_per_service means each service manages its own database connection pool, sized independently based on that service's concurrency needs.
- **dps_011** (d2): backup_and_recovery_scope defines that each service backs up and restores only its own database, making recovery operations independent across services.
- **dps_012** (d2): service_catalog_entry is the registration of a service's database connection metadata (host, port, credentials ref) in a service_discovery registry, so authorized services or operators can locate it.
- **dps_007** (d2): api_composition is the pattern where a client or gateway aggregates data from multiple service databases by querying each service's API and combining results, compensating for the lack of cross-service SQL joins.
- **dps_009** (d3): migration_orchestration is the process of evolving a service's schema independently, typically done via versioned migration scripts (e.g., Flyway, Liquibase) that each service applies on its own schedule.
- **gateway_routing__integration** (d5): Integration with load_balancing to distribute requests across multiple instances of a backend service.
- **gateway_routing_backend_service** (d5): A microservice or backend resource that receives forwarded requests from the gateway.
- **gateway_routing_circuit_breaker_integration** (d5): Integration with circuit_breaker logic to prevent routing to failing backend services.
- **gateway_routing_fallback_route** (d5): A predefined route or behavior triggered when primary routing fails or no route matches.
- **gateway_routing_response_aggregation** (d5): The combination of responses from multiple backend services into a single client response.
- **gateway_routing_reverse_proxy** (d5): The mechanism that forwards matched requests to backend services and returns responses to clients.
- **gateway_routing_route** (d5): A defined mapping between incoming request criteria and a target backend service endpoint.
- **gateway_routing_service_discovery_integration** (d5): Integration with service_discovery to dynamically resolve backend service network locations.
- **gateway_routing_header_transformation** (d6): The addition, removal, or modification of HTTP headers during request forwarding.
- **gateway_routing_path_rewrite** (d6): A transformation that modifies the request path before forwarding to the backend service.
- **gateway_routing_route_definition** (d6): The declarative or imperative specification of a route including matching criteria and target service.
- **gateway_routing_request_matcher** (d7): A component that evaluates incoming requests against route matching criteria.
- **gateway_routing_route_priority** (d7): The ordering rule that determines which route takes precedence when multiple routes match.

### from `software_architecture_patterns_and_styles`
- **event_streaming** (d2): A data handling approach where events are captured in order as an immutable log (stream), allowing multiple consumers to read independently (e.g., Kafka, Pulsar).
- **message_queue** (d2): A communication mechanism where messages are placed in a queue by producers and consumed asynchronously by consumers, decoupling sender and receiver in time and space.
- **publish_subscribe_pattern** (d2): A messaging pattern where publishers send messages to a topic without knowing subscribers, and subscribers receive messages published to topics they are interested in.
- **saga_pattern** (d2): A pattern for managing distributed transactions across microservices using a sequence of local transactions with compensating actions for rollback, replacing distributed transactions.
- **service_discovery** (d3): The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
- **api_gateway** (d3): A server entry point that routes requests to backend services, handling cross-cutting concerns like authentication, rate_limiting, and protocol_translation.
- **choreography_pattern** (d3): A distributed coordination pattern where services exchange events without a central orchestrator; each service knows what to do based on received events.
- **orchestration_pattern** (d3): A distributed coordination pattern where a central coordinator (orchestrator) directs the flow of operations across services, contrasting with choreography.
- **load_balancing** (d4): A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
- **gateway_routing** (d4): A pattern where an API_gateway routes requests to appropriate backend services based on request characteristics (URL path, headers) without the client knowing service locations.
- **rate_limiting** (d4): A traffic_management technique that controls how many requests a client can make in a given time period, protecting services from overload and abuse.
- **event_driven_architecture** (d4): A software design pattern where the flow of the program is determined by events (user actions, sensor outputs, messages) and the propagation of events through the system.
- **service_oriented_architecture** (d4): An architectural pattern where application components provide services to other components via a communication protocol, typically over a network. SOA emphasizes interoperability and composition of services.
- **horizontal_scaling** (d5): Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
- **auto_scaling** (d6): Automatically adjusting the number of compute instances based on demand metrics (CPU, request_count, queue_depth), improving resource efficiency.

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*