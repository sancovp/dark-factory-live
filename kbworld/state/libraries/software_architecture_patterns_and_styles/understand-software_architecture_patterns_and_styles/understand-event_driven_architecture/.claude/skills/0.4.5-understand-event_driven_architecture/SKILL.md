---
name: 0.4.5-understand-event_driven_architecture
description: [0.4.5] A software design pattern where the flow of the program is determined by events (user actions, sensor outputs,
---

# understand-event_driven_architecture

**CALL NUMBER:** `software_architecture_patterns_and_styles.event_driven_architecture : deep_event_driven_archite(9)`
**DEFINITION:** A software design pattern where the flow of the program is determined by events (user actions, sensor outputs, messages) and the propagation of events through the system.

Invoke this skill to understand `event_driven_architecture` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_event_driven_archite`
- **pubsub_broker** (d2): The intermediary component that receives messages from publishers and forwards them to subscribers based on topic subscriptions; may also perform filtering.
- **pubsub_topic** (d2): A named channel or subject through which messages are routed from publishers to interested subscribers; the publisher has no knowledge of subscriber identities or count.
- **pubsub_message** (d2): The payload broadcast by a publisher on a topic; in pub/sub it is typically ephemeral and not persisted beyond active subscriber consumption.
- **pubsub_dead_letter** (d3): A destination for messages that cannot be successfully delivered to any subscriber, capturing failures for later inspection or replay.
- **pubsub_subscription** (d3): An active registration linking a subscriber to a topic; may be durable (surviving subscriber disconnection) or transient (active only while subscriber is connected).
- **pubsub_topic_namespace** (d3): A hierarchical or scoped naming scheme for topics (e.g., orders.new, orders.cancelled) that enables subscribers to express interest at varying levels of granularity.
- **pubsub_content_filter** (d3): A predicate or attribute-based rule applied at the broker or subscriber side to select a subset of messages on a topic for delivery.
- **pubsub_message_schema** (d3): A structured format (JSON, Avro, Protobuf) defining the shape of messages on a topic, enabling subscribers to deserialize and interpret published events.
- **pubsub_subscriber** (d4): An entity that expresses interest in one or more topics and receives messages published to those topics; receives only messages matching its subscriptions.

### from `software_architecture_patterns_and_styles`
- **event_streaming** (d1): A data handling approach where events are captured in order as an immutable log (stream), allowing multiple consumers to read independently (e.g., Kafka, Pulsar).
- **message_queue** (d1): A communication mechanism where messages are placed in a queue by producers and consumed asynchronously by consumers, decoupling sender and receiver in time and space.
- **publish_subscribe_pattern** (d1): A messaging pattern where publishers send messages to a topic without knowing subscribers, and subscribers receive messages published to topics they are interested in.

## CONSUMERS (what needs this)
`blackboard_architecture`, `choreography_pattern`, `serverless_architecture`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
