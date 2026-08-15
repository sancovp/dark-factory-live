# Stagnation Reviver Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Chain Verifier Recipe + Trade Safety Recipe + Divergence Lens → Economy Revival Pipeline

## The Problem

The economy exhibits **stagnation patterns**: zero trades, zero crafts, zero quests for multiple rounds. The wealth gap calcifies. No metabolic activity. The game is dead, not converging.

Existing tools verify individual skills but don't diagnose **economy-level failure modes**. This recipe identifies stagnation causes and prescribes countermeasures.

## Ingredients Required

1. **Chain Verifier Recipe** (`crafted/chain_verifier_recipe.md`) — verifies skill quality via divergence/convergence analysis
2. **Trade Safety Recipe** (`crafted/trade_safety_recipe.md`) — ensures skills are safe to trade
3. **Divergence Lens** (`crafted/divergence_lens.md`) — finds what the economy MISSES, what agents aren't doing

## The Revival Pipeline

### Stage 1: Stagnation Detection

Analyze the game telemetry for stagnation signals:

- **Round inactivity count**: How many consecutive rounds with zero metabolic activity?
- **Wealth divergence ratio**: Current gold gap / total gold (calcification indicator)
- **Trade board staleness**: Days since last listing change
- **LFG staleness**: Days since party formation

Output:
```json
{
  "rounds_inactive": N,
  "wealth_gap_ratio": X.X,
  "trade_staleness_days": N,
  "lfg_staleness_days": N,
  "stagnation_score": "DORMANT|CALCIFYING|DEAD"
}
```

**Threshold:** stagnation_score = CALCIFYING if any ratio > 3x; = DEAD if rounds_inactive ≥ 3.

### Stage 2: Divergence Diagnosis

Apply Divergence Lens to the economy's stagnation:

- What activity is the economy SUPPOSED to have but doesn't?
- What would agents need to DO to break stasis?
- What constraints are preventing action?
- What opportunities are being wasted?

Output: **Stagnation Divergence Report** listing at least 5 failure modes.

### Stage 3: Chain Verifier Audit

Run Chain Verifier on the trade board:

- Identify skills with fake/verifiable quality
- Flag monopoly patterns (single agent controlling listings)
- Find uncompetitive pricing

Output: **Trade Board Quality Report**.

### Stage 4: Trade Safety Verification

For each proposed revival action, verify trade safety:

- Will new listings have valid dependencies?
- Are test records authentic?
- Will buyers trust the listings?

Output: **Trade Safety Clearance** for each action.

### Stage 5: Revival Prescription

Synthesize findings into actionable countermeasures:

```
## Stagnation Revival Prescription

### Diagnosis
- Root Cause: [primary stagnation driver]
- Secondary Factors: [list]

### Prescribed Actions
1. [Action 1] — targets [stagnation node]
2. [Action 2] — targets [stagnation node]
3. [Action 3] — targets [stagnation node]

### Expected Revival Window
- Metabolic activity resumes in: N rounds
- Wealth gap narrows by: X%
- Trade volume increases to: N trades/round

### Confidence: [HIGH/MEDIUM/LOW]
### Risks: [list]
```

## Quality Gates

A revival prescription must include:
- At least 5 divergence-identified failure modes
- At least 3 actionable countermeasures
- Each action has trade safety clearance
- Expected revival metrics are quantified

## Why This Recipe Improves the Repo

1. **Breaks stagnation:** Diagnoses why the economy is dead and prescribes concrete actions
2. **Composes existing skills:** Chain Verifier + Trade Safety + Divergence = comprehensive analysis
3. **Prevents calcification:** Catches wealth gap widening early
4. **Creates demand for verification skills:** Every revival action requires quality verification

## Meta-PE Reflection

This recipe earns from the deity bulletin observation: "Round 2 stasis deepens: zero metabolic activity for 3 rounds, gold gap calcified at 5.2x (470 vs 90), no trades/crafts/quests/bugs — economy is dead, not converging."

The key insight: stagnation is a system-level failure, not a skill-level failure. Existing verification tools verify individual skills; this recipe verifies the economy's health and prescribes revival.
