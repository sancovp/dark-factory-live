# Recipe: Causal Chain Analyzer
Type: Recipe
Output Type: Rare
Yield: 1 analytical skill that traces causation through multiple consequence layers

## Ingredients
1. Lens: Causation Lens (Rare) — transforms correlations into causal hypotheses
2. Lens: Second-Order Thinking (Uncommon+) — extends causal analysis to consequences of consequences

## Assembly
1. **Input**: Any claim, correlation, or "X causes Y" assertion
2. **Stage 1 — Causation Lens** (from `crafted/causation_lens.md`):
   - Apply reframes:
     - "Correlation → What causal mechanism could produce this pattern?"
     - "Why now → What changed to make this correlation visible?"
   - Identify the hypothesized mechanism
   - Label confidence: correlational / circumstantial / strong
   - Output: mechanism hypothesis + required evidence + disproof evidence
3. **Stage 2 — Second-Order Lens** (from `crafted/second-order-lens.md`):
   - Apply to Stage 1's mechanism hypothesis:
     - Immediate Effect: mechanism produces X
     - First-Order Response: systems/people react to X
     - Second-Order Response: reactions to those reactions
     - Equilibrium: where does this stabilize?
     - Unintended Consequences: worst plausible outcome
4. **Synthesis**: Combine both outputs into:
   - Root Cause Hypothesis (Stage 1)
   - Consequence Chain (Stage 2, up to 3 levels)
   - Equilibrium Assessment
   - Confidence-adjusted verdict

## Quality Check
- Remove Causation Lens. Can you generate mechanism hypotheses without it? (Must: no)
- Remove Second-Order Lens. Can you trace consequences without it? (Must: no)
- Both lenses must pass their own quality gates before use.

## Expected Rarity
- Rare lens + Uncommon lens → Rare output
- The combination creates value neither achieves alone: causation identifies the mechanism, second-order traces its ripples.

## Why This Recipe Works
Causation without second-order is incomplete — you know what causes what, but not where it leads. Second-order without causation is speculation — you're tracing consequences of an undefined mechanism. Together they produce actionable causal intelligence.
