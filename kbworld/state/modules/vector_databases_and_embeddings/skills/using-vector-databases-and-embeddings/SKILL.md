---
name: using-vector-databases-and-embeddings
description: "Use the vector databases and embeddings neurosymbolic module: RAG library, agent brain, growable KB — proof-checked"
version: 0.1.0
---

# using-vector-databases-and-embeddings

This module is a CULTIVATED, PROOF-CHECKED knowledge organism about
**vector databases and embeddings** (262 concepts / 150 relations; grown by a
KB factory — every region admitted by a Prolog consistency gate, wrongness
tracked as open supersede-issues, never hidden).

## The four ways to use it

1. **As RAG** — the sibling `understand-{x}` skills in this plugin,
   coordinate-addressed (call number = home class : dependency facets — the
   import web, literally); FTS5 index via `skilltree.build_index` over
   `${CLAUDE_PLUGIN_ROOT}/skills/using-vector-databases-and-embeddings/references/skilltree.json`.
2. **As an agent (the runnable brain SHIPS here)** — the neuromorphic brain
   is bundled at `${CLAUDE_PLUGIN_ROOT}/skills/using-vector-databases-and-embeddings/data/brain/`
   (kuzu `neurodb` = the activation graph + `tissue/` = the gyri). Point a
   `KbcBrain` at it and `brain_ask("your question")`: the graph FIRES the
   matching gyri numerically (spreading activation, weights decide — not an
   agent choosing), each fired gyrus answers over its territory, the
   synthesis is PROVEN one level up (the SES tower — the join is a theorem),
   and the prover teaches the graph back (Hebbian). Needs `kuzu` +
   `brain-agent` + `ee_v2.kbc` installed.
3. **As tools your agents hold** — `ee_v2.kbc.heaven_tools.make_kbc_tools`
   over this module's data root
   (`${CLAUDE_PLUGIN_ROOT}/skills/using-vector-databases-and-embeddings/data/`): 14 heaven tools
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

- `vector_databases_and_embeddings.vector_database`
- `vector_databases_and_embeddings.approximate_nearest_neighbor`
- `vector_databases_and_embeddings.faiss`
- `deep_vector_database.chroma_collection`
- `vector_databases_and_embeddings.nearest_neighbor_search`
- `vector_databases_and_embeddings.hnsw_index`
- `vector_databases_and_embeddings.ivf_index`
- `vector_databases_and_embeddings.product_quantization`
- `vector_databases_and_embeddings.sentence_embedding`
- `vector_databases_and_embeddings.embedding_model`
- `vector_databases_and_embeddings.semantic_search`
- `vector_databases_and_embeddings.vector_embedding`
