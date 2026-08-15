---
name: 0.2.1-understand-pubsub_broker
description: [0.2.1] The intermediary component that receives messages from publishers and forwards them to subscribers based on to
---

# understand-pubsub_broker

**CALL NUMBER:** `deep_event_driven_archite.pubsub_broker`
**DEFINITION:** The intermediary component that receives messages from publishers and forwards them to subscribers based on topic subscriptions; may also perform filtering.

Invoke this skill to understand `pubsub_broker` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_event_driven_archite`
- **pubsub_dead_letter** (d1): A destination for messages that cannot be successfully delivered to any subscriber, capturing failures for later inspection or replay.
- **pubsub_message** (d1): The payload broadcast by a publisher on a topic; in pub/sub it is typically ephemeral and not persisted beyond active subscriber consumption.
- **pubsub_subscription** (d1): An active registration linking a subscriber to a topic; may be durable (surviving subscriber disconnection) or transient (active only while subscriber is connected).
- **pubsub_content_filter** (d2): A predicate or attribute-based rule applied at the broker or subscriber side to select a subset of messages on a topic for delivery.
- **pubsub_message_schema** (d2): A structured format (JSON, Avro, Protobuf) defining the shape of messages on a topic, enabling subscribers to deserialize and interpret published events.
- **pubsub_subscriber** (d2): An entity that expresses interest in one or more topics and receives messages published to those topics; receives only messages matching its subscriptions.
- **pubsub_topic_namespace** (d2): A hierarchical or scoped naming scheme for topics (e.g., orders.new, orders.cancelled) that enables subscribers to express interest at varying levels of granularity.

## CONSUMERS (what needs this)
`es_stream_broker`, `event_streaming`, `pubsub_message_schema`, `pubsub_topic`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
