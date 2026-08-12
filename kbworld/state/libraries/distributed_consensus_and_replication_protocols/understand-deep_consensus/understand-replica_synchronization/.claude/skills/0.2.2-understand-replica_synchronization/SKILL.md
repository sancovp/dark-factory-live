---
name: 0.2.2-understand-replica_synchronization
description: [0.2.2] Propagation of updates to ensure all replicas converge toward identical state.
---

# understand-replica_synchronization

**CALL NUMBER:** `deep_consensus.replica_synchronization : distributed_consensus_and_replication_protocols(8)`
**DEFINITION:** Propagation of updates to ensure all replicas converge toward identical state.

Invoke this skill to understand `replica_synchronization` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_consensus`
- **gossip_dissemination** (d1): Probabilistic epidemic protocol spreading updates through pairwise exchanges.
- **view_change** (d6): Transition of consensus membership to new configuration after membership modification.

### from `distributed_consensus_and_replication_protocols`
- **anti_entropy** (d1): Repair of divergent replicas by comparing Merkle trees and exchanging differences.
- **read_repair** (d1): Background correction of stale replicas when read reveals outdated data.
- **state_transfer** (d2): Sending full current state to a lagging replica for rapid catch-up.
- **eventual_consistency** (d2): Given no new updates, all replicas will eventually converge to the same value.
- **catch_up_recovery** (d3): Process of syncing a lagging or new replica with current leader state.
- **reconfiguration** (d4): Process of changing cluster membership while maintaining consistency guarantees.
- **membership_change** (d5): Adding or removing nodes from the cluster without service interruption.
- **joint_consensus** (d6): Raft's two-phase configuration change using joint configuration of old and new members.

## CONSUMERS (what needs this)
`primary_backup`, `state_machine_replication`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
