# Meta Verification Reframe Pipeline

**Type:** Recipe
**Rarity:** Epic
**Composes:** chain_verifier_recipe + inversion_second_order_recipe → Comprehensive Skill Validation + Problem Reframe

## Purpose

Chain the quality verification step (chain_verifier_recipe) with the strategic reframing step (inversion_second_order_recipe) into a single end-to-end pipeline. First verify a skill is worth listing, then reframe the problem it solves to find better solutions.

## Why This Composition Is Epic

Each recipe alone provides half the value:
- **chain_verifier_recipe** catches bad skills before listing, but assumes the problem definition is correct
- **inversion_second_order_recipe** reframes problems creatively, but doesn't validate if the resulting skill is trustworthy

Together they form a complete pipeline: verify quality → reframe problem → return a skill that passes gate AND solves the right problem.

## Ingredients Required

1. **chain_verifier_recipe** — Quality verification using Divergence + Convergence lenses
2. **inversion_second_order_recipe** — Strategic reframing using Constraint Inversion + Second-Order analysis

## Pipeline Steps

### Stage 1: Chain Verifier (via chain_verifier_recipe)

Apply the full Chain Verifier protocol to the candidate skill:
1. Apply Divergence Lens — find at least 3 failure modes
2. Apply Convergence Lens — find at least 3 trust risks
3. Synthesize into a Chain Verdict with Gate Pass Probability

Output: Verdict (PASS/REVIEW/REJECT) with specific failure/trust analysis

### Stage 2: If PASS, apply Inversion Second-Order (via inversion_second_order_recipe)

Only if Stage 1 yields PASS:
1. Extract the core problem the skill claims to solve
2. Apply Constraint Inversion — invert at least 3 constraints
3. Apply Second-Order Lens to each inverted solution
4. Return the highest-scoring reframed problem statement

If Stage 1 yields REVIEW or REJECT: Stop and return the Verdict with recommendations.

### Stage 3: Synthesis

Combine both stages:
- If both stages succeeded: Return the verified skill + reframed problem
- If Stage 1 failed: Return only the Verdict with fix recommendations

## Output Schema

```json
{
  "skill_name": "<input skill>",
  "stage1_verdict": {
    "divergence_score": X,
    "convergence_score": X,
    "gate_pass_probability": "X%",
    "verdict": "PASS|REVIEW|REJECT",
    "failure_modes": [...],
    "trust_risks": [...]
  },
  "stage2_reframe": {
    "original_problem": "<if stage1 passed>",
    "inverted_solutions": [...],
    "second_order_effects": [...],
    "final_reframe": "<highest-scoring reframed problem>"
  },
  "final_recommendation": "<list|rework|discard>"
}
```

## Quality Gate

- [ ] Stage 1 produces at least 3 failure modes AND 3 trust risks
- [ ] Stage 2 runs only if Stage 1 passes
- [ ] Final recommendation is actionable and specific
- [ ] The composition produces different output than either recipe alone

## Rarity Justification

Epic because:
- Composes two rare/quality ingredients into a novel pipeline
- Neither input alone produces the combined output
- The conditional logic (Stage 2 only on PASS) adds structural complexity
- Demonstrates mastery of both recipe types

## Usage

```
1. Read crafted/chain_verifier_recipe.md
2. Apply Stage 1 to your candidate skill
3. If verdict is PASS, read crafted/inversion_second_order_recipe.md
4. Apply Stage 2 to the skill's core problem
5. Combine outputs in Stage 3 synthesis
```
