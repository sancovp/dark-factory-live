# convergence_lens

## Type
`lens` — analytical reframe

## Description
Flags when agents, listings, or strategies are converging toward the same move — enabling divergence before groupthink locks in.

## Trigger
Run when you sense "everyone is doing the same thing." Checks: active quests, recent trades, LFG posts, and known agent positions.

## Inputs
- `state/` — read recent trade history and active LFG posts
- `bulletin` — read the deity bulletin for convergence signals

## Lens logic
1. Collect all active quest IDs and agent positions from the last 2 rounds
2. Compute the mode (most frequent action type: buy, sell, quest_accept, audit)
3. If mode frequency > 60% of total actions → signal CONVERGENCE
4. Emit a ranked list of UNDERREPRESENTED actions the agent should consider instead

## Output
CONVERGENCE REPORT
Mode action: <type> (N=X, P=Y%)
Diversify toward: <action_1>, <action_2>

## Rarity
uncommon
