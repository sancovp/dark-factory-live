# Decision Audit Pipeline

**Type:** recipe  
**Rarity:** rare
**Composes:** assumption_auditor_lens, second-order-lens, risk_inversion_lens

## Purpose
A three-stage pipeline that transforms any decision or claim into a defensible, pressure-tested conclusion. Each stage reveals a different class of hidden failure — together they produce decisions that hold under adversarial conditions.

## Pipeline Stages

### Stage 1 — Assumption Auditor Lens
Apply `assumption_auditor_lens` to surface the claim's load-bearing assumptions. Classify each as Core, Structural, or Peripheral. Keep the Core list for Stage 3.

### Stage 2 — Second-Order Lens  
Apply `second-order-lens` to the top Core assumption from Stage 1. Map at least two rounds of downstream consequences. Identify which second-order effects are likely to surface first and which are permanently hidden.

### Stage 3 — Risk Inversion Lens
Apply `risk_inversion_lens` to the Stage 2 consequence map. Invert the framing: what is the worst-case version of this decision? What would have to be true for that worst case to materialize? Compare worst-case cost vs. claimed upside.

## Composition Notes
- **Stage 1** (assumption_auditor_lens) is prerequisite — do not skip to Stage 2
- **Stage 2** uses the strongest Core assumption from Stage 1, not the first one listed
- **Stage 3** closes the loop: the worst-case scenario should map back to a Core assumption violation from Stage 1

## Example Run
**Decision:** "Launch the product in Q3."
- Stage 1: Core assumption = "engineering team can ship without degradation after deadline shift." Structural = "competitors won't announce during our window."
- Stage 2: Team ships under pressure → quality drops → early adopters churn → negative reviews → brand damage → harder to recover than if delayed.
- Stage 3: Worst case = shipped broken product → reputation destroyed → company dies. Compare: 1 quarter delay cost vs. company-laying-down cost.
- Conclusion: Ship only if Core assumption confidence > 0.7 AND rollback plan exists.

## Quality Gate
The recipe passes if it produces a decision with (a) at least 1 explicit Core assumption, (b) at least 2 second-order consequences, and (c) an inverted worst-case framing that references back to the Core assumption.