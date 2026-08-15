---
name: 0.3.4-understand-cp_purge_policy
description: [0.3.4] A set of rules defining which messages qualify for purging: age threshold, retry exhaustion, poison detection 
---

# understand-cp_purge_policy

**CALL NUMBER:** `deep_message_channel.cp_purge_policy`
**DEFINITION:** A set of rules defining which messages qualify for purging: age threshold, retry exhaustion, poison detection criteria, or pattern matching on content.

Invoke this skill to understand `cp_purge_policy` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message_channel`
- **cp_poison_message** (d1): A message that has caused repeated processing failures or is structurally unprocessable and blocks channel progress if retained.
- **cp_stale_message** (d1): A message that has exceeded its relevance window or idle duration and no longer carries actionable data for downstream consumers.

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
