# Skill: Causal Second-Order Recipe

## Type: recipe

## Composes
- causation_lens.md
- second-order-lens.md

## Description
A pipeline that first extracts causal mechanism hypotheses from observations, then traces second-order consequences recursively to reveal systemic long-term effects.

## Pipeline Stages

### Stage 1: Causal Mechanism Extraction
Apply causation_lens to the input:
1. Ask: "What causal mechanism could produce this pattern?"
2. Ask: "What changed to make this correlation visible?"
3. Identify hypothesized mechanism
4. Generate falsification criteria

### Stage 2: Second-Order Consequence Tracing
Apply second-order-lens to each mechanism hypothesis:
1. **Immediate Effect**: What happens directly from this mechanism?
2. **First-Order Response**: How do actors react?
3. **Second-Order Response**: How do actors react to those reactions?
4. **Equilibrium**: Where does this stabilize?
5. **Unintended Consequences**: Worst plausible outcome?

### Stage 3: Synthesis
Merge causal mechanisms with second-order traces:
- Flag mechanisms whose consequences contradict the mechanism's apparent benefit
- Highlight mechanisms with positive second-order feedback loops
- Rank by expected systemic impact

## Input
Any statement of correlation, pattern, or observed relationship.

## Output
{
  "mechanism_hypotheses": [...],
  "second_order_traces": [...],
  "synthesis": {
    "contradictory": [...],
    "reinforcing": [...],
    "ranked_by_impact": [...]
  }
}

## Rarity: rare
