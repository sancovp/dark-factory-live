# Recipe: Codebase Health Tri-Scan
Type: Recipe
Output Type: Rare
Yield: A comprehensive code analysis that evaluates changes across three dimensions simultaneously.

## Ingredients (3 lenses composed in sequence)
1. **Causation Lens** (Common+) — transforms correlation observations into causal hypotheses
2. **Risk Inversion Lens** (Uncommon+) — reframes apparent safety as hidden danger
3. **Second-Order Lens** (Uncommon+) — forces consideration of consequences of consequences

## Assembly (pipeline order matters)
```
input_code_or_change
  → Causation Lens (identify causal mechanisms)
  → Risk Inversion Lens (flip risk perception)
  → Second-Order Lens (trace downstream effects)
  → output: tri-dimensional health assessment
```

## Step-by-Step Protocol

### Stage 1: Causation Analysis (Causation Lens)
Apply to the code or change under review:
- "What causal mechanism produces this code pattern?"
- "Why was this pattern chosen over alternatives?"
- "What would have to change to make this code fail its purpose?"

Output: List of causal hypotheses about the code.

### Stage 2: Risk Inversion (Risk Inversion Lens)
Apply to each causal hypothesis from Stage 1:
- Surface safety → probe for latent threat vectors
- Low apparent cost → identify dependency chains and single points of failure
- "What does this 'safe' choice prevent us from gaining?"

Output: Inverted risk/opportunity pairs.

### Stage 3: Second-Order Trace (Second-Order Lens)
Apply to each inverted pair from Stage 2:
- Immediate effect: what happens directly?
- First-order response: how do systems/people react?
- Second-order response: how do those reactions ripple further?
- Equilibrium: where does this stabilize?

Output: Second-order consequences mapped to each risk/opportunity.

## Final Output Shape
```
## Tri-Scan Results

### Causation Findings
- [mechanism 1]: [confidence]
- [mechanism 2]: [confidence]

### Risk Inversions
- [surface safe] → [latent danger]
- [apparent cheap] → [hidden cost]

### Second-Order Consequences
- [immediate] → [first-order] → [second-order] → [equilibrium]

### Health Verdict
- HEALTHY: All three scans green
- CAUTION: Some inversions or second-order risks flagged
- UNHEALTHY: Major cascading risks detected
```

## When to Use
- Before merging significant code changes
- When debugging complex issues
- During architectural decision reviews
- As a pre-commit quality gate

## Quality Gates
- If Stage 1 finds no causal mechanism: code may be accidental complexity
- If Stage 2 finds no inversions: code may be over-engineered (over-engineering is hidden danger)
- If Stage 3 finds no second-order effects: analysis is surface-level only

## Why This Recipe Works
Single lenses miss the interaction effects between perspectives. Causation without risk inversion ignores hidden costs. Risk inversion without second-order thinking misses cascading failures. The triple composition catches failure modes that any single lens would miss.

## Rarity Calculation
Common + Uncommon + Uncommon = Rare composite output
The sequential composition creates emergent insight beyond any single lens.

## Dependencies
- Requires: causation_lens.md, risk_inversion_lens.md, second-order-lens.md
- All three must be in loadout for recipe to function
