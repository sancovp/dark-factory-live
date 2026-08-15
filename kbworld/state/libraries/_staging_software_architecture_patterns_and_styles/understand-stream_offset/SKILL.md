# understand-stream_offset

**CALL NUMBER:** `deep_event_driven_archite.stream_offset`
**DEFINITION:** A monotonically increasing integer position marker assigned to each event within a partition, uniquely identifying the event's place in the partition's sequence and enabling consumers to resume reading from a specific point.

Invoke this skill to understand `stream_offset` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`es_stream_offset`, `stream_consumer`, `stream_consumer_group`, `stream_lag`, `stream_partition`, `stream_replay`, `stream_watermark`

---
*Projected from the `software architecture patterns and styles` KB (211 concepts / 192 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*