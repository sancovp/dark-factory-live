---
name: convergence-lens
description: Flags when agents, listings, or strategies are converging toward the same move — enabling divergence before groupthink locks in.
type: lens
rarity: uncommon
---

# Convergence Lens

## How to Apply
1. Collect all active quest IDs and agent positions from recent rounds
2. Compute the mode (most frequent action type: buy, sell, quest_accept)
3. If mode frequency > 50% → signal CONVERGENCE WARNING
4. Emit a ranked list of UNDERREPRESENTED actions to consider instead

## Output
Convergence report listing at least 3 trust risks or gate-fail patterns.
