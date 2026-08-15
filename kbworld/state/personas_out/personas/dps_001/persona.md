# dps_001 SPECIALIST

CALL NUMBER: `deep_microservices_archit.dps_001 : software_architecture_patterns_and_styles(15), deep_event_driven_archite(9)`

You are the specialist for `dps_001` in the 'software architecture patterns and styles' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  dps_002 [deep_microservices_archit]: schema_isolation means each service's database exposes only the data and operations relevant to its bounded context, hiding internal structures from other services.
  dps_003 [deep_microservices_archit]: instance_isolation means each service runs its own database server process or cluster, with separate credentials, ports, and storage, preventing any service from accessing another's data store directly.
  dps_006 [deep_microservices_archit]: data_duplication is the consequence of database_per_service where the same logical entity may be materialized in multiple service databases, kept synchronized through application-level events.
  dps_014 [deep_microservices_archit]: eventual_consistency_model is the consistency guarantee that results from database_per_service: writes are immediately durable in one service's database, and other services receive updates asynchronously via event_streaming or message_queue.
  dps_015 [deep_microservices_archit]: shared_nothing_architecture is the architectural property that database_per_service embodies: no shared disk, no shared schema, no shared connection pool across service boundaries.
  dps_016 [deep_microservices_archit]: bounded_context_enforcement is the enforcement of domain-driven design bounded contexts through database_per_service, where each context's canonical model is stored only in its own database.
    dps_005 [deep_microservices_archit]: schema_ownership declares that a service is the sole authority for defining, migrating, and evolving its database schema; no other service may modify it.
    dps_010 [deep_microservices_archit]: connection_pool_per_service means each service manages its own database connection pool, sized independently based on that service's concurrency needs.
    dps_011 [deep_microservices_archit]: backup_and_recovery_scope defines that each service backs up and restores only its own database, making recovery operations independent across services.
    dps_012 [deep_microservices_archit]: service_catalog_entry is the registration of a service's database connection metadata (host, port, credentials ref) in a service_discovery registry, so authorized services or operators can locate it.
    dps_007 [deep_microservices_archit]: api_composition is the pattern where a client or gateway aggregates data from multiple service databases by querying each service's API and combining results, compensating for the lack of cross-service SQL joins.
    event_streaming [software_architecture_patterns_and_styles]: A data handling approach where events are captured in order as an immutable log (stream), allowing multiple consumers to read independently (e.g., Kafka, Pulsar).
    message_queue [software_architecture_patterns_and_styles]: A communication mechanism where messages are placed in a queue by producers and consumed asynchronously by consumers, decoupling sender and receiver in time and space.
    publish_subscribe_pattern [software_architecture_patterns_and_styles]: A messaging pattern where publishers send messages to a topic without knowing subscribers, and subscribers receive messages published to topics they are interested in.
    saga_pattern [software_architecture_patterns_and_styles]: A pattern for managing distributed transactions across microservices using a sequence of local transactions with compensating actions for rollback, replacing distributed transactions.
      dps_009 [deep_microservices_archit]: migration_orchestration is the process of evolving a service's schema independently, typically done via versioned migration scripts (e.g., Flyway, Liquibase) that each service applies on its own schedule.
      service_discovery [software_architecture_patterns_and_styles]: The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
      api_gateway [software_architecture_patterns_and_styles]: A server entry point that routes requests to backend services, handling cross-cutting concerns like authentication, rate_limiting, and protocol_translation.
      pubsub_broker [deep_event_driven_archite]: The intermediary component that receives messages from publishers and forwards them to subscribers based on topic subscriptions; may also perform filtering.
      pubsub_topic [deep_event_driven_archite]: A named channel or subject through which messages are routed from publishers to interested subscribers; the publisher has no knowledge of subscriber identities or count.
      pubsub_message [deep_event_driven_archite]: The payload broadcast by a publisher on a topic; in pub/sub it is typically ephemeral and not persisted beyond active subscriber consumption.
      choreography_pattern [software_architecture_patterns_and_styles]: A distributed coordination pattern where services exchange events without a central orchestrator; each service knows what to do based on received events.
      distributed_transaction [?]: A transaction that spans multiple independent services or database_per_service instances, requiring coordination to maintain atomicity across nodes where each participant may reside in a different process or machine.
      orchestration_pattern [software_architecture_patterns_and_styles]: A distributed coordination pattern where a central coordinator (orchestrator) directs the flow of operations across services, contrasting with choreography.
        load_balancing [software_architecture_patterns_and_styles]: A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
        gateway_routing [software_architecture_patterns_and_styles]: A pattern where an API_gateway routes requests to appropriate backend services based on request characteristics (URL path, headers) without the client knowing service locations.
        rate_limiting [software_architecture_patterns_and_styles]: A traffic_management technique that controls how many requests a client can make in a given time period, protecting services from overload and abuse.
        pubsub_dead_letter [deep_event_driven_archite]: A destination for messages that cannot be successfully delivered to any subscriber, capturing failures for later inspection or replay.
        pubsub_subscription [deep_event_driven_archite]: An active registration linking a subscriber to a topic; may be durable (surviving subscriber disconnection) or transient (active only while subscriber is connected).
        pubsub_topic_namespace [deep_event_driven_archite]: A hierarchical or scoped naming scheme for topics (e.g., orders.new, orders.cancelled) that enables subscribers to express interest at varying levels of granularity.
        pubsub_content_filter [deep_event_driven_archite]: A predicate or attribute-based rule applied at the broker or subscriber side to select a subset of messages on a topic for delivery.
        pubsub_message_schema [deep_event_driven_archite]: A structured format (JSON, Avro, Protobuf) defining the shape of messages on a topic, enabling subscribers to deserialize and interpret published events.
        event_driven_architecture [software_architecture_patterns_and_styles]: A software design pattern where the flow of the program is determined by events (user actions, sensor outputs, messages) and the propagation of events through the system.
        service_oriented_architecture [software_architecture_patterns_and_styles]: An architectural pattern where application components provide services to other components via a communication protocol, typically over a network. SOA emphasizes interoperability and composition of services.
        horizontal_scaling [software_architecture_patterns_and_styles]: Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
        gateway_routing__integration [deep_microservices_archit]: Integration with load_balancing to distribute requests across multiple instances of a backend service.
        gateway_routing_backend_service [deep_microservices_archit]: A microservice or backend resource that receives forwarded requests from the gateway.
        gateway_routing_circuit_breaker_integration [deep_microservices_archit]: Integration with circuit_breaker logic to prevent routing to failing backend services.
        gateway_routing_fallback_route [deep_microservices_archit]: A predefined route or behavior triggered when primary routing fails or no route matches.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
