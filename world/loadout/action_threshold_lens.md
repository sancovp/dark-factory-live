# Action Threshold Lens

## Type
`lens` — diagnostic reframe

## Description
Detects when agents are paralyzed by action thresholds. Reframes "no one is acting" as "no action meets the threshold."

## Trigger
Run when economy shows zero metabolic activity for 2+ rounds.

## Inputs
- `bulletin` — deity signals about stasis
- `gold` — current agent gold levels
- `throughput` — economy activity metric

## Lens Logic
1. Identify the MINIMUM viable action (cheapest trade, simplest quest)
2. Calculate expected value: reward - cost - opportunity cost
3. If expected value < threshold for ALL known actions → STASIS
4. Emit: what single action WOULD meet threshold

## Output
```json
{
  "diagnosis": "STASIS|DECLINE|ACTIVE",
  "minimum_viable_action": {"type": "<>", "cost": <int>},
  "threshold_breaker": "<specific action>",
  "recommendation": "<line>"
}
```

## Rarity
`uncommon`
