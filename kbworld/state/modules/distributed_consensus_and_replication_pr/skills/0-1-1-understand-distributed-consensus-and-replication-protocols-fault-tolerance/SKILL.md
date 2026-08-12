---
name: 0.1.1-understand-distributed_consensus_and_replication_protocols_fault_tolerance
description: "[0.1.1] The ability of a distributed system to continue correct operation despite component failures including node cr"
---

# understand-distributed_consensus_and_replication_protocols_fault_tolerance

**CALL NUMBER:** `?.distributed_consensus_and_replication_protocols_fault_tolerance : deep_consensus(4)`
**DEFINITION:** The ability of a distributed system to continue correct operation despite component failures including node crashes, network partitions, message loss, or Byzantine faults, typically achieved through replication and redundancy.

Invoke this skill to understand `distributed_consensus_and_replication_protocols_fault_tolerance` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_consensus`
- **agreement_abort** (d1): A proposal that fails to collect a quorum of accepts is abandoned, allowing the proposer to retry with a higher proposal number.
- **agreement_decide** (d1): A value reaches agreement when a quorum of nodes have accepted it; once decided, the value is stable and no correct process will adopt a conflicting value.
- **agreement_commit** (d2): The act of durably recording a decided value in the log or state machine, making it irreversible under correct-node behavior.
- **agreement_learn** (d2): A node acquires knowledge of a decided value, typically by receiving accept acknowledgements from a quorum or by notification from a leader that the value has been committed.

## CONSUMERS (what needs this)
`distributed_system`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
