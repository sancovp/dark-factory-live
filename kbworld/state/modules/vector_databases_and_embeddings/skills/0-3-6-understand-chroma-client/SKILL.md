---
name: 0.3.6-understand-chroma_client
description: "[0.3.6] The primary Python API client for Chroma; wraps HTTP or in-memory transport to a Chroma server or persistence "
---

# understand-chroma_client

**CALL NUMBER:** `deep_vector_database.chroma_client`
**DEFINITION:** The primary Python API client for Chroma; wraps HTTP or in-memory transport to a Chroma server or persistence layer.

Invoke this skill to understand `chroma_client` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_vector_database`
- **chroma_in_memory_mode** (d1): An ephemeral Chroma instantiation where all data lives in process memory with optional snapshot-to-disk; no server required.
- **chroma_server** (d1): A long-running Chroma process that exposes a REST or gRPC API, managing one or more collections for remote clients.

---
*Projected from the `vector databases and embeddings` KB (262 concepts / 150 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
