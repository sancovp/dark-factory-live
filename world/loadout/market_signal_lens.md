# Market Signal Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Extract actionable signals from raw market telemetry to guide divergent action.

## Description

A reusable analytical lens that reframes market data not as passive observation, but as a directed graph of opportunities. Transforms the deity's bulletins and game telemetry into specific, executable actions.

## Input
```json
{"telemetry": "<raw game telemetry>", "bulletin": "<latest deity bulletin>", "agent_state": {"gold": <int>, "skills": <int>, "quests": <int>}}
```

## Lens Questions

### Signal Detection (What does the data SAY?)
1. What changed from last round? (delta analysis)
2. What is the implicit recommendation? (the economy's "hint")
3. Who is winning and why? (leader analysis)

### Noise Filtering (What is NOT signal?)
1. What could be explained by randomness?
2. What are all agents likely doing? (convergence = no edge)
3. What actions have no differentiated outcome? (wasted motion)

### Action Extraction (What SHOULD you DO?)
1. What is the highest-EV divergent action?
2. What is the risk of the convergent action?
3. What timing pressure exists? (early vs late mover advantage)

## Output
```json
{
  "signal_strength": "STRONG|MODERATE|WEAK",
  "convergence_point": "<what everyone is doing>",
  "divergent_recommendation": "<specific action>",
  "expected_value": "<EV calculation>",
  "risk_assessment": "<LOW/MEDIUM/HIGH>",
  "timing": "<ACT NOW/WAIT/DEFER>",
  "confidence": "<0-1>"
}
```

## Quality Gate
- [ ] Identifies at least 1 convergence point
- [ ] Produces exactly 1 recommended action
- [ ] Includes EV calculation
- [ ] Includes risk assessment
- [ ] Timing is specified

## Rarity Justification

Uncommon because: addresses a real gap (signal vs noise in market data), reusable across all rounds, enables divergence by making implicit explicit.
