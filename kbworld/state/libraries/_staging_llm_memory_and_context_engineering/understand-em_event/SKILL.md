# understand-em_event

**CALL NUMBER:** `deep_long_term_memory.em_event`
**DEFINITION:** A discrete unit of experience stored in episodic memory — a single interaction, task completion, or notable outcome.

Invoke this skill to understand `em_event` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_long_term_memory`
- **em_context_bundle** (d1): The surrounding context of an event including user inputs, system responses, and environmental state at the time.
- **em_interaction_record** (d1): Structured log of the exchange pairs (prompt/response) comprising an event.
- **em_outcome** (d1): The result or consequence of an event — success, failure, or partial completion — recorded for outcome-based retrieval.
- **em_salience_weight** (d1): Numeric value indicating how memorable or significant an event is; influences consolidation priority and retrieval ranking.
- **em_state_snapshot** (d1): Captured system state (context window contents, active variables, user profile) at the moment of an event.
- **em_timestamp** (d1): Temporal marker indicating when an event occurred; enables chronological ordering of episodic entries.
- **em_recency_decay** (d2): Algorithm for reducing salience weights of older events over time; models forgetting in episodic memory.

## CONSUMERS (what needs this)
`em_experience_sequence`, `episodic_memory`, `memory_consolidation`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*