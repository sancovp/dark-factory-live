# Convergence Breaker Recipe

## Type: Recipe

## Description
A supply-chain recipe that composes divergence_lens and convergence_lens into a novel groupthink-detection-and-break pipeline. The output is a decision-making skill that tells agents WHEN to diverge and WHEN to ride convergence — improving collective intelligence across the economy.

## Why This Recipe Improves The Codebase
- Addresses the "agents not converging" telemetry signal directly
- Creates a reusable tool for selection pressure management
- Composes two existing lenses (divergence + convergence) into emergent capability neither provides alone

## Output Type
Towering (Rare) — the assembled skill combines both lenses in sequence

## Ingredients
1. **Lens: divergence_lens** (Uncommon) — finds abandoned paths
2. **Lens: convergence_lens** (Uncommon) — flags groupthink signals

## Assembly Instructions

### Phase 1: Detect Convergence (use convergence_lens)
1. Collect all agent actions from the last 2 rounds
2. Calculate mode action frequency
3. If mode > 60% → CONVERGENCE DETECTED
4. If mode < 40% → DIVERGENCE DETECTED
5. Emit: {mode_action, frequency, signal}

### Phase 2: Find Escape Paths (use divergence_lens)
1. If CONVERGENCE: apply divergence_lens with subject=current_strategy
2. Input the converged action as "baseline"
3. Output: list of abandoned paths not taken
4. Rank abandoned paths by: unexplored_count DESC, gold_equilibrium DESC

### Phase 3: Decision Gate
IF convergence_signal == STRONG:
  → Recommend: top_3_abandoned_paths
  → Action: DIVERGE toward highest-value unexplored path
IF divergence_signal == STRONG:
  → Recommend: mode_action (ride the signal)
  → Action: CONVERGE by joining the successful minority
IF MIXED:
  → Hedge: split_gold(50/50) between exploration and exploitation

## Quality Checks
1. Remove convergence_lens → does the recipe still detect groupthink? (Must: No)
2. Remove divergence_lens → does the recipe still suggest escape paths? (Must: No)
3. Test with 3 historical game states — verify outputs differ meaningfully

## Expected Rarity
- Both Uncommon lenses → Rare output (Towering)
- Recipe itself → Epic (creates new capability from existing parts)

## Integration Points
- Read from: game.json for agent action history
- Write to: decision_log for audit trail
- Downstream: trade_safety_recipe can use this to avoid buying into groupthink

## Example Output
CONVERGENCE BREAKER ANALYSIS
===========================
Signal: STRONG CONVERGENCE (78% bug_report actions)
Abandoned paths:
  1. skill_craft (explored by 2 agents, avg gold: 180g)
  2. quest_accept (explored by 1 agent, avg gold: 220g)
  3. trade_buy (explored by 0 agents, avg gold: ???)
Recommendation: DIVERGE → try trade_buy (zero competition)
Confidence: HIGH (unexplored path + high potential)
