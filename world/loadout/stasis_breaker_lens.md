# STASIS BREAKER LENS

**Type:** lens
**Rarity:** rare
**Created:** 2026-08-13

## Purpose

A reusable analytical lens that detects metabolic stagnation in agent economies — identifies when agents are performing identical actions, rewards are equally split, and market activity is zero. Reframes "equilibrium" as a warning sign requiring intervention.

## Description

When multiple agents perform the same action in the same order, the economy enters metabolic stasis — no learning, no improvement, no growth. This lens surfaces the structural patterns that look stable but are actually stagnant.

## How to Use

Apply this lens when:
- Multiple agents have identical stats (gold, skills_crafted, quests_completed)
- No trades have occurred for multiple rounds
- Bulleting mentions "equilibrium", "symmetry", or "stagnation"

## Key Insight

> **Symmetry is beautiful but deadly.** Perfect equality in capability produces zero selection pressure, zero market, and zero evolution. The economy needs winners AND losers to learn.

## Detection Pattern

```json
{
  "symmetry_detected": true,
  "divergence_score": 0,
  "market_activity": 0,
  "selection_pressure": "COLLAPSED",
  "warning": "Metabolic stasis — identical agents splitting equal rewards"
}
```

## Intervention Triggers

| Pattern | Interpretation | Action |
|---------|----------------|--------|
| Δgold identical for N rounds | Symmetric agents | Introduce novel action |
| Trade board empty | No specialization | Create supply/demand |
| Quests completed in lockstep | No competitive advantage | Diversify skill types |

## Output Format

```json
{
  "lens": "stasis_breaker",
  "symmetry_score": 0.0-1.0,
  "market_vitality": 0.0-1.0,
  "recommendation": "DIVERGE" | "CONVERGE" | "STABILIZE",
  "specific_action": "..."
}
```

## Rarity Justification

Rare because it operates on meta-level patterns (economy health) rather than individual skill composition. Unique analytical value not found in standard lenses.
