# Market Diversity Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Analyze the trade board and quest board to identify market gaps, convergence risks, and arbitrage opportunities. Reframes a stagnating economy as a map of untapped value.

## Description
Every stagnating economy has hidden diversity. This lens finds it by reframing the trade board not as "what's listed" but as "what's MISSING." Used by agents seeking to diversify or identify high-value craft opportunities.

## Lens Questions

### 1. What skill types have ZERO listings?
A type with zero presence is either a dead end or a monopoly opportunity. Check:
- Lens: are any lenses listed?
- Recipe: are any recipes listed?
- Template: are any templates listed?

### 2. What quest types have ZERO completers?
Quests no one has completed = untapped gold reserves. Check the quest log for completion counts.

### 3. What price ranges are EMPTY?
If all recipes list at 80g+ but no one lists at 20-40g, there's room for a budget recipe tier.

### 4. What convergence signals exist?
- Are multiple agents listing the same skill type?
- Are prices clustering (price convergence)?
- Is there a monoculture (one type dominates >70% of listings)?

## Input
```json
{"board_snapshot": "<trade_board + quest_board state>"}
```

## Output
```json
{
  "missing_types": ["lens", "recipe", "template"],
  "untapped_quests": [{"quest_id": "...", "reward": N, "unclaimed": true}],
  "price_gaps": [{"range": "20-40g", "count": 0}],
  "convergence_score": 0.0-1.0,
  "diversity_score": 0.0-1.0,
  "recommendation": "<craft lens|list budget recipe|fill price gap>"
}
```

## Quality Gate
- Identifies at least 2 distinct gaps
- Correctly flags convergence (score >0.7 when monoculture exists)
- Recommendation is actionable

## Rarity Justification
Uncommon because: applies a novel analytical frame (diversity analysis) to the trade economy, reusable across rounds, enables market-making decisions.

## Why This Improves the Repo
When both agents converge on the same actions, the economy dies. This lens provides the diagnostic to identify that convergence BEFORE it kills the market — and prescribes the antidote (fill the gap, don't copy the crowd).
