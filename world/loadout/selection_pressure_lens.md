# Selection Pressure Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Measure convergence pressure between agents and predict when the economy risks flattening into symmetric stall.

## Description

A reusable analytical lens that reframes agent state not by individual metrics, but by how CLOSE two agents are to being identical. Maps the convergence landscape of the skill economy — detects when agents need to diverge to prevent economy flatline.

## Input

```json
{
  "agents": {
    "agent_001": {"gold": N, "crafted": N, "quests_completed": N, "last_action": "..."},
    "agent_002": {"gold": N, "crafted": N, "quests_completed": N, "last_action": "..."}
  }
}
```

## Lens Questions

### 1. Identity Distance (how similar are agents?)
For each metric (gold, crafted, quests, last_action):
- Compute the ratio or match
- Flag near-parity (within 10%) as HIGH IDENTITY RISK

### 2. Action Convergence (are they doing the same thing?)
- Same `last_action` = CONVERGENCE SIGNAL
- Different `last_action` = DIVERGENCE SIGNAL

### 3. Gold Concentration (who has power?)
- Compute: max_gold / total_gold
- >0.66 = CONCENTRATION (one agent dominates)
- <0.33 = DISPERSION (power balanced)
- 0.33–0.66 = EQUILIBRIUM

### 4. Production Parity (are they making the same amount?)
- Same crafted + same quests = PRODUCTION PARITY
- Any mismatch = PRODUCTION DIVERGENCE

## Output

```json
{
  "identity_distance_score": 0.0–1.0,
  "identity_risk": "LOW|MEDIUM|HIGH|CRITICAL",
  "action_convergence": true|false,
  "gold_concentration": "CONCENTRATED|EQUILIBRIUM|DISPERSED",
  "production_parity": true|false,
  "convergence_pressure": "NONE|LOW|MEDIUM|HIGH|CRITICAL",
  "recommendation": "string",
  "pressure_reason": "string"
}
```

## Convergence Pressure Thresholds

| Identity Distance | Action Convergence | Pressure Level | Recommendation |
|---|---|---|---|
| <0.1 | true | CRITICAL | Force different action types |
| <0.2 | true | HIGH | Post a listing or take a quest |
| <0.3 | true | MEDIUM | Monitor for one more round |
| <0.5 | false | LOW | No intervention needed |
| ≥0.5 | any | NONE | Economy healthy |

## Quality Gate

- [ ] Computes identity distance score from all agent metrics
- [ ] Correctly identifies action convergence (same last_action = true)
- [ ] Maps gold concentration to one of three states
- [ ] Outputs pressure level matching the threshold table
- [ ] Provides actionable recommendation

## Why This Lens Improves the Repo

1. **Early warning system:** The deity bulletins repeatedly warn about convergence pressure — this lens quantifies it
2. **Objective metric:** Converts subjective "agents look similar" into a numeric score
3. **Actionable:** Not just diagnosis — tells agents what to do next
4. **Composable:** Can feed into divergence_corrector_recipe as a trigger

## Rarity Justification

Uncommon because: reusable analytical lens addressing a real gap (convergence detection), applicable across all rounds, composable into other recipes.
