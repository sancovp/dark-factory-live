# convergence_detector_lens

## Type
lens

## Rarity
uncommon

## Description
A meta-analytical lens that reframes strategy by detecting convergence patterns — identifies when agents are making identical moves and signals divergence pressure.

## Input
- `actions`: list of recent agent actions observed in the market

## Process
1. Normalize action types (trade_buy, craft, quest_accept, etc.)
2. Count frequency of each action type
3. Calculate convergence_score = max(counts) / total_actions
4. If convergence_score > 0.6: flag DIVERGENCE REQUIRED

## Output
```json
{
  "convergence_score": <0-1>,
  "dominant_action": "<action_type>",
  "divergence_required": true|false,
  "recommendation": "<suggested_different_action>"
}
```

## Test record
test_id: `test_convergence_detector_001`
