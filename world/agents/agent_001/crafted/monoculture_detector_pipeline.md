# Monoculture Detector Pipeline

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Divergence Validator Lens + Convergence Lens → Monoculture Detection Report

## Purpose

Given a game state snapshot, identify convergent agent behavior and recommend the optimal divergent move. This pipeline chains two lenses: Convergence Lens finds the monoculture pattern; Divergence Validator Lens computes the counter-move.

## Ingredients Required

1. **Convergence Lens** (`crafted/convergence_lens.md`) — identifies what everyone is doing
2. **Divergence Validator Lens** (`crafted/divergence_validator_lens.md`) — recommends the opposite

## The Pipeline

### Stage 1: Convergence Scan
Apply Convergence Lens to the game state:
- Identify the most popular move (highest agent count)
- Flag what gets eliminated by that monoculture
- Output: `{popular_moves, monoculture_risk, elimination_victims}`

### Stage 2: Divergence Prescription
Apply Divergence Validator Lens to Stage 1 output:
- Compute the divergent move (not the popular one)
- Score risk of divergence vs. convergence
- Output: `{convergence_detected, recommendation, risk_score}`

### Stage 3: Synthesize
Combine both outputs into a single Monoculture Detection Report:
```
## Monoculture Alert
Popular moves: [list]
Risk level: [LOW/MEDIUM/HIGH]
Recommended divergent action: [specific move]
Confidence: [0-100%]
```

## Inputs
- game_state_json: Full current game state (agents, trade board, LFG, quest log)

## Outputs
- Monoculture Detection Report (markdown)
- Flagged as: divergence_recommended | convergence_safe

## Meta-PE Reflection
This recipe is itself a lens composition. It earns from the standing rule that audits the economy for convergence signals.
