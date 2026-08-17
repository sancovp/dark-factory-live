# Recipe: Root Cause Risk Pipeline
Type: Recipe
Output Type: Epic

## Composition
Chains two lenses in sequence to transform surface observations into actionable risk insights:
1. **causation_lens** — transforms correlations into causal hypotheses with mechanism
2. **risk_inversion_lens** — inverts perceived risks to find hidden opportunities

## Pipeline Logic
```
input_observation
  → causation_lens (find root mechanism)
  → risk_inversion_lens (invert risks to find opportunities)
  → output: root-caused opportunity map
```

## Ingredients Required
- causation_lens.md (Rare) — root cause identification
- risk_inversion_lens.md (Uncommon) — risk/opportunity inversion

## Assembly Steps
1. **Capture Surface Observation**
   - Record the correlation, pattern, or symptom to analyze
   - Tag as: [SURFACE-FINDING]

2. **Apply Causation Lens**
   - Ask: "What causal mechanism could produce this?"
   - Ask: "What changed to make this visible now?"
   - Record mechanism hypothesis
   - Mark output: [ROOT-HYPOTHESIS]

3. **Apply Risk Inversion Lens to Root Hypothesis**
   - Surface risk: The root cause could cause X
   - Invert: What opportunity does preventing X create?
   - Surface safety: The root cause seems stable
   - Invert: What hidden danger lies in assuming stability?

4. **Synthesize Output**
   - Root mechanism (from step 2)
   - Risk/opportunity pairs (from step 3)
   - Confidence level: correlational / circumstantial / strong
   - Action: which opportunities are actionable given current resources?

## Quality Check
- Remove causation_lens: Do you have mechanism without root cause? (Must: no)
- Remove risk_inversion_lens: Do you have root cause without opportunity? (Must: no)
- Both lenses required: the composition creates value neither has alone

## Rarity Derivation
- Rare lens + Uncommon lens → Epic output
- Chain creates emergent analytical capability

## Use Cases
- Auditing codebase for systemic risks
- Analyzing trade failures for hidden patterns
- Post-mortem root cause with opportunity mapping
