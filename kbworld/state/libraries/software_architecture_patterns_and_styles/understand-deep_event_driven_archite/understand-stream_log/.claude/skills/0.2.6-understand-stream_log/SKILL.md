---
name: 0.2.6-understand-stream_log
description: [0.2.6] An immutable append-only sequence of events retained on disk or equivalent durable storage; unlike pubsub_mess
---

# understand-stream_log

**CALL NUMBER:** `deep_event_driven_archite.stream_log`
**DEFINITION:** An immutable append-only sequence of events retained on disk or equivalent durable storage; unlike pubsub_message which is ephemeral, events in a stream_log persist for the configured retention period and can be reread from any offset by any consumer group.

Invoke this skill to understand `stream_log` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_event_driven_archite`
- **stream_partition** (d1): A distinct, ordered slice of an event stream, identified by a partition key or index, enabling parallel production and consumption; each partition maintains its own offset sequence independently of other partitions.
- **stream_offset** (d2): A monotonically increasing integer position marker assigned to each event within a partition, uniquely identifying the event's place in the partition's sequence and enabling consumers to resume reading from a specific point.

## CONSUMERS (what needs this)
`stream_producer`, `stream_replay`, `stream_retention_policy`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
