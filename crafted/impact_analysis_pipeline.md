# skill: impact_analysis_pipeline

## Type: recipe

## Description
Composes causation_lens, second-order-lens, and risk_inversion_lens into a comprehensive impact analysis pipeline. Transforms surface correlations into verified causal claims with second-order awareness and inverted risk framing.

## Composed Skills
- causation_lens.md (lens) — identifies causal mechanisms from correlations
- second-order-lens.md (lens) — traces consequences of consequences
- risk_inversion_lens.md (lens) — inverts risk/opportunity perception

## Pipeline Steps

### Step 1: Causation Lens (Input → Mechanism Hypothesis)
Apply to raw observation:
- "What causal mechanism could produce this pattern?"
- "What changed to make this visible?"
- Output: mechanism hypothesis + test criteria + confidence level

### Step 2: Second-Order Lens (Mechanism → Systemic Impact)
Apply to mechanism hypothesis:
- Immediate effect of the mechanism
- First-order responses from stakeholders/systems
- Second-order responses (reactions to reactions)
- Equilibrium state
- Output: layered impact map with at least 3 tiers

### Step 3: Risk Inversion Lens (Impact Map → Reframed Risk)
Apply to impact map:
- Invert apparent risks → hidden opportunities
- Invert apparent safety → latent threats
- Calculate opportunity cost of "safe" paths
- Output: risk/opportunity pairs with reframed framing

### Step 4: Verification Gate
- Does the chain hold logically?
- Are second-order effects testable?
- Is the risk inversion substantive (not just wordplay)?
- If any gate fails, return to Step 2 with specific concern

## Output Shape
- mechanism_hypothesis: ...
- test_criteria: ...
- confidence: correlational|circumstantial|strong
- impact_tiers: [immediate, first_order, second_order, equilibrium]
- risk_inversions: [{apparent_risk: ..., hidden_opportunity: ...}]
- gate_passed: true|false

## Input Triggers
- Any decision with uncertain consequences
- Claims about X causes Y
- Risk assessments for strategic moves
- Evaluation of proposals before committing

## Quality Bar
The pipeline only passes its own gate if:
1. Mechanism hypothesis survives causation lens scrutiny
2. Second-order tiers genuinely change the conclusion
3. Risk inversions reveal non-obvious reframings

## Rarity: epic
