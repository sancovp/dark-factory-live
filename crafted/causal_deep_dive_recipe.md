# Recipe: Causal Deep Dive Pipeline
Type: Recipe
Rarity: rare

## What It Does
Composes second-order-lens and causation-lens into a pipeline that transforms surface claims into deep causal understanding. First maps systemic consequences, then traces back to root mechanisms.

## Composition
1. **second-order-lens** (from crafted/second-order-lens.md) — identifies consequences of consequences
2. **causation-lens** (from crafted/causation_lens.md) — traces causal mechanisms

## Pipeline Logic
```
input_claim
  → second-order-lens (map the consequence chain)
  → causation-lens (identify mechanisms that produced chain)
  → output: defended causal hypothesis
```

## Ingredients
- A claim, decision, or hypothesis to analyze
- 10 minutes of structured thinking time

## Assembly Steps
1. **Capture the Claim**: Write the original claim verbatim
2. **Apply Second-Order Lens**:
   - What happens immediately?
   - How do systems/people react?
   - How do they react to those reactions?
   - Where does this stabilize?
   - What are unintended consequences?
3. **Apply Causation Lens to the Second-Order Output**:
   - What causal mechanism could produce this consequence chain?
   - What changed to make this mechanism visible now?
   - What evidence would disprove this mechanism?
4. **Synthesize**: Combine into a defended hypothesis with:
   - The mechanism (from causation-lens)
   - The evidence chain (from second-order-lens)
   - Confidence level

## Example
**Input**: "We should cut QA to ship faster"

**After Second-Order Lens**: Immediate: faster shipping, reduced cost. First-order: more bugs reach users. Second-order: user trust erodes, support load increases, team morale drops. Equilibrium: slower overall + reputation damage.

**After Causation Lens**: Mechanism hypothesis: cutting QA removes the feedback loop that catches regressions early. What changed: deadline pressure masked the cost. Disproof: if bugs don't increase, QA wasn't catching real issues.

**Synthesis**: Cutting QA ships faster SHORT-TERM but breaks the regression-detection mechanism, causing slower delivery LONG-TERM. Confidence: circumstantial (depends on bug rate in current QA).

## Quality Check
- Does the second-order lens reveal something non-obvious? (No → the claim is too vague)
- Does the causation lens find a mechanism, not just correlation? (No → keep iterating)
- Is the final hypothesis actionable? (No → the analysis is academic)

## Why This Recipe Works
Second-order lens alone shows where things go. Causation lens alone shows why. Together they produce hypotheses with both direction AND mechanism — claims that can be tested and defended.
