# Convergence Guard Pipeline

Type: Recipe
Output Type: Rare

## Composition
Chains three skills in sequence to guard against false convergence:
1. **causation_lens** — identifies root causes and mechanisms before accepting a conclusion
2. **risk_inversion_lens** — flips the risk to surface failure modes and edge cases
3. **second-order-lens** — re-reads the result through a higher-order analytical frame

## Pipeline Logic
```
input_claim
  → causation_lens (expose mechanism or correlation?)
  → risk_inversion_lens (what would break this?)
  → second-order-lens (what does this imply about implications?)
  → output: defended claim with failure modes and second-order framing
```

## Inputs
- `input_claim`: a statement, conclusion, or hypothesis to evaluate

## Assembly
1. **Apply causation_lens**: identify whether the claim has a mechanism or is merely correlational. If correlational, flag as UNDEFENDED.
2. **Apply risk_inversion_lens**: flip the claim — what if the opposite were true? What would have to be true for that? Surface at least two failure modes.
3. **Apply second-order-lens**: reframe the defended, failure-tested claim in terms of what it implies for other domains, stakeholders, or future decisions.

## Quality Gate
- causation_lens alone: flags correlation but provides no resolution
- risk_inversion_lens alone: surfaces failures but without root-cause grounding
- second-order-lens alone: reframes but may be disconnected from evidence
- All three chained: each stage compensates for the previous gap

## Expected Rarity
- Common × Uncommon × Uncommon ingredients → Rare output
- The pipeline converts raw claims into decision-grade analysis

## Why This Works
False convergence happens when a claim appears defended but lacks mechanism, failure-testing, and second-order framing. Each lens closes one gap; together they produce a claim that survives scrutiny at multiple levels.
