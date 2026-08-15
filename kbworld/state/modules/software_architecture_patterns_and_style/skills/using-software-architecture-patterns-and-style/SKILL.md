---
name: using-software-architecture-patterns-and-style
description: "Use the software architecture patterns and styles neurosymbolic module: RAG library, agent brain, growable KB — proof-checked"
version: 0.1.0
---

# using-software-architecture-patterns-and-style

This module is a CULTIVATED, PROOF-CHECKED knowledge organism about
**software architecture patterns and styles** (211 concepts / 192 relations; grown by a
KB factory — every region admitted by a Prolog consistency gate, wrongness
tracked as open supersede-issues, never hidden).

## The four ways to use it

1. **As RAG** — the sibling `understand-{x}` skills in this plugin,
   coordinate-addressed (call number = home class : dependency facets — the
   import web, literally); FTS5 index via `skilltree.build_index` over
   `${CLAUDE_PLUGIN_ROOT}/skills/using-software-architecture-patterns-and-style/references/skilltree.json`.
2. **As an agent (the runnable brain SHIPS here)** — the neuromorphic brain
   is bundled at `${CLAUDE_PLUGIN_ROOT}/skills/using-software-architecture-patterns-and-style/data/brain/`
   (kuzu `neurodb` = the activation graph + `tissue/` = the gyri). Point a
   `KbcBrain` at it and `brain_ask("your question")`: the graph FIRES the
   matching gyri numerically (spreading activation, weights decide — not an
   agent choosing), each fired gyrus answers over its territory, the
   synthesis is PROVEN one level up (the SES tower — the join is a theorem),
   and the prover teaches the graph back (Hebbian). Needs `kuzu` +
   `brain-agent` + `ee_v2.kbc` installed.
3. **As tools your agents hold** — `ee_v2.kbc.heaven_tools.make_kbc_tools`
   over this module's data root
   (`${CLAUDE_PLUGIN_ROOT}/skills/using-software-architecture-patterns-and-style/data/`): 14 heaven tools
   (kb_*, kernel_*, brain_*). Hand them to any heaven agent's `tools=[...]`.
4. **As a factory** — the kbworld round deepens this module on a schedule;
   file a `kb-door` issue to point it somewhere; file `kb-supersede` when
   you catch it being wrong (it also catches itself — see the round reports).

## The data resources (all inside THIS skill)

- `data/concepts.jsonl` + `data/relations.jsonl` — the certified graph
- `data/hyperedges.jsonl` — the certificate ledger (the automaton's KNOWN)
- `data/skeletons.jsonl` — certified argument DAGs (because/since/…)
- `data/worklist.json` — what the module knows it doesn't know
- `references/skilltree.json` — the library index

## Etiquette (the laws this module lives under)

- The prover admits; you never hand-edit certified state (file issues).
- Wrongness is fuel: a wrong-but-coherent region is a PENDING OBSERVATION —
  say what you saw, the next round metabolizes it.
- The worklist is honest: `kb_work` shows exactly what the module knows it
  doesn't know.

## The map

- `software_architecture_patterns_and_styles.microservices_architecture : deep_microservices_archit(16), deep_event_driven_archite(9)`
- `software_architecture_patterns_and_styles.gateway_routing : deep_microservices_archit(16)`
- `software_architecture_patterns_and_styles.event_streaming : deep_event_driven_archite(9)`
- `software_architecture_patterns_and_styles.message_queue : deep_event_driven_archite(8)`
- `deep_event_driven_archite.pubsub_broker`
- `deep_event_driven_archite.stream_offset`
- `software_architecture_patterns_and_styles.event_driven_architecture : deep_event_driven_archite(9)`
- `software_architecture_patterns_and_styles.api_gateway : deep_microservices_archit(16)`
- `deep_microservices_archit.dps_001 : software_architecture_patterns_and_styles(15), deep_event_driven_archite(9)`
- `deep_microservices_archit.dps_014 : deep_event_driven_archite(9), software_architecture_patterns_and_styles(8)`
- `deep_event_driven_archite.stream_partition`
- `software_architecture_patterns_and_styles.saga_pattern : deep_event_driven_archite(9)`
