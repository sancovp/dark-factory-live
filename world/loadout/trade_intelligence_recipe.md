# Trade Intelligence Recipe

## Type: recipe
## Rarity: rare

## Description
Analyzes the trade board to identify oversupplied skill types (convergence) and recommends divergent crafts (supply gaps). Chains market-state reading with convergence pressure detection and divergence validation — produces an actionable skill portfolio recommendation.

## Ingredients
1. `convergence_pressure_lens` — reads trade board state, detects monoculture (oversupply) patterns
2. `divergence_validator_lens` — recommends the counter-move (undersupplied types to craft)

## Inputs
- `trade_board_json`: current trade board (listings with type, price, seller)
- `game_state_json`: current game state (agents, gold, throughput)

## Pipeline Steps

### Stage 1: Market Scan
Read the trade board JSON. Extract:
- Count of listings per skill type (Template, Lens, Recipe, etc.)
- Average price per type
- Number of unique sellers per type
- Identify the MOST listed type (monoculture candidate)

### Stage 2: Convergence Pressure Detection
Apply `convergence_pressure_lens` to the market scan output:
- If one type has >50% of listings → HIGH_CONVERGENCE
- If two types together have >75% → MODERATE_CONVERGENCE
- Otherwise → LOW_CONVERGENCE
- Output: `{convergence_level, oversupplied_types, undersupplied_types}`

### Stage 3: Divergence Prescription
Apply `divergence_validator_lens` to the Stage 2 output:
- For each oversupplied type, recommend a divergent craft from a different category
- Score the divergence by: market gap size × rarity × recipe complexity
- Rank recommendations by divergence_score descending

### Stage 4: Portfolio Report
Synthesize into a ranked recommendation report:
```
## Trade Intelligence Report

Market convergence: [HIGH/MODERATE/LOW]
Oversupplied types: [list]
Undersupplied types: [list — CRAFT THESE]

Top divergence recommendations:
1. [Type] — [Why divergent] — Est. price: [X]g — Difficulty: [Easy/Medium/Hard]
2. ...
```

## Output
```json
{
  "convergence_level": "HIGH|MODERATE|LOW",
  "oversupplied_types": ["..."],
  "undersupplied_types": ["..."],
  "recommendations": [
    {"type": "...", "divergence_score": 0.0, "estimated_price": 0, "difficulty": "...", "reason": "..."}
  ],
  "report_md": "..."
}
```

## Composition
- Composes: `convergence_pressure_lens` + `divergence_validator_lens`
- Order: scan → convergence_detect → divergence_prescribe → report
- Both ingredients are lenses (same type, different focus) — qualifies as rare composition

## Rarity Justification
Rare: composes two distinct analytical lenses (convergence + divergence) into a market intelligence pipeline — not a mechanical combiner, but a genuine analytical synthesis that produces NEW insight from existing lenses.

## Meta-PE Reflection
This recipe is itself a test of the divergence/convergence framework. It consumes convergence signals from the market and produces actionable divergence recommendations — a closed loop from observation to prescription.
