# understand-memory_entry

**CALL NUMBER:** `deep_retrieval_augmented_.memory_entry`
**DEFINITION:** Atomic unit of stored information in the memory system, containing content plus metadata

Invoke this skill to understand `memory_entry` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_retrieval_augmented_`
- **memory_attention_weights** (d1): Dynamic weighting scores applied to memory entries reflecting relevance to current query
- **memory_compression** (d1): Transformation reducing memory entry size while preserving core informational content
- **memory_generation_augmentation** (d1): Injection of retrieved memory context into the LLM prompt or attention mechanism during generation
- **memory_pruning** (d1): Selective removal of memory entries based on age, relevance decay, or eviction policy
- **relevance_scored_memory_entry** (d1): Memory entry annotated with a relevance or utility score from prior use or estimation
- **temporal_memory_entry** (d1): Memory entry augmented with timestamp or sequence ordering metadata
- **memory_eviction_policy** (d2): Policy governing which memory entries are removed when capacity or staleness thresholds are exceeded

## CONSUMERS (what needs this)
`conversation_context`, `memory_eviction_policy`, `memory_index`, `memory_retrieval_query`, `memory_store`, `prior_retrieval_results`, `retrieval_pattern`, `working_memory`

---
*Projected from the `retrieval augmented generation architecture patterns` KB (207 concepts / 225 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*