# Convergence Breaker Lens

**Type:** Lens
**Rarity:** Rare

## Purpose

A lens that actively breaks convergence by finding the most DIVERGENT path available. Where other agents see symmetry, this lens spots the whitespace — the unsaturated move that the deity rewards.

## The Problem

Convergence is invisible until it's too late. By the time you notice "everyone is doing the same thing," you're already punished. This lens works proactively: it finds divergence BEFORE you commit.

## The Lens Questions

For any decision point, ask:

1. **Market Gaps:** What skills/quests are UNCLAIMED by other agents this round?
2. **Symmetry Check:** Am I about to mirror what agent_002 is doing? If so, find the inverse.
3. **Timing Signal:** Is this a first-move or follower's move? First movers get the whitespace; followers get convergence risk.

## Input

```yaml
game_state:
  agent_metrics: {gold: int, skills_crafted: int, quests_completed: int}
  other_agent_metrics: {gold: int, skills_crafted: int, quests_completed: int}
  available_quests: [list of quest objects]
  trade_board: [list of listings]
  round_number: int
```

## Output

```yaml
{
  "convergence_risk": "high/medium/low",
  "unsaturated_moves": ["quest_id_1", "lens", "recipe"],
  "recommended_action": "DIVERGE by doing X",
  "symmetry_score": 0.0-1.0,
  "whitespace_identified": true/false
}
```

## Decision Matrix

| Agent A State | Agent B State | Recommended Action |
|---------------|---------------|-------------------|
| Same quest | Same quest | Find different quest |
| Same skill type | Same skill type | Different type (lens vs recipe) |
| Similar gold | Similar gold | Quest completion for gold divergence |

## Divergence Triggers

The lens FLAGS convergence when:
- `|gold_a - gold_b| <= 10` → convergence risk
- `skills_crafted_a == skills_crafted_b` → symmetry detected  
- Same quest accepted in same round → guaranteed convergence

## Composition Use

This lens COMPOSES with convergence_detector_lens for a full monoculture pipeline:
- convergence_detector_lens: detects what IS happening
- convergence_breaker_lens: recommends what to do INSTEAD

## Tags

lens, divergence, convergence, strategy, economy
