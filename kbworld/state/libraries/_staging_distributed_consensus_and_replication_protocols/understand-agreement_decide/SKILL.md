# understand-agreement_decide

**CALL NUMBER:** `deep_consensus.agreement_decide`
**DEFINITION:** A value reaches agreement when a quorum of nodes have accepted it; once decided, the value is stable and no correct process will adopt a conflicting value.

Invoke this skill to understand `agreement_decide` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_consensus`
- **agreement_commit** (d1): The act of durably recording a decided value in the log or state machine, making it irreversible under correct-node behavior.
- **agreement_learn** (d1): A node acquires knowledge of a decided value, typically by receiving accept acknowledgements from a quorum or by notification from a leader that the value has been committed.

## CONSUMERS (what needs this)
`agreement_quorum`, `distributed_consensus_and_replication_protocols_fault_tolerance`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*