# Gate Prep Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** `chain_verifier_recipe` + `lens_second_order_inversion` → Skill Gate-Readiness Pipeline

## Purpose

Prepare any crafted skill for the gate test by running quality verification, then applying second-order inversion to the skill's core problem statement — surfacing hidden failure modes and hidden assumptions that would cause gate rejection.

## Ingredients

1. **chain_verifier_recipe** — Quality verification using Divergence + Convergence lenses
2. **lens_second_order_inversion** — Reframes problem statements via inverted outcome analysis

## The Pipeline

### Stage 1: Chain Verification (via chain_verifier_recipe)

Apply the full Chain Verifier protocol to the candidate skill:
1. Apply Divergence Lens — find at least 3 failure modes the skill doesn't address
2. Apply Convergence Lens — find at least 3 trust risks or convergence patterns
3. Synthesize into a Chain Verdict: PASS / REVIEW / REJECT

**Output:** Verdict + list of specific failure modes and trust risks

### Stage 2: Second-Order Inversion (via lens_second_order_inversion)

Only run if Stage 1 yields PASS or REVIEW:
1. Extract the skill's stated core problem (from the ## Purpose / ## Description section)
2. Apply the lens protocol to that problem statement:
   - State the desired outcome for the skill
   - Invert it completely
   - Ask second-order why (what causes the inverted outcome?)
   - Extract inverse requirements
   - Map to first-order actions
3. Return the reframed problem + action list

If Stage 1 yields REJECT: Stop and return the Verdict with fix recommendations.

### Stage 3: Gate-Readiness Synthesis

Combine both outputs:
- **If both stages succeeded:** Return gate-ready skill with verified problem + reframed problem statement
- **If Stage 1 failed:** Return only the Verdict with fix recommendations

## Output Schema

```json
{
  "skill_name": "<input skill>",
  "stage1_verdict": {
    "verdict": "PASS|REVIEW|REJECT",
    "failure_modes": ["..."],
    "trust_risks": ["..."],
    "chain_verdict": "<synthesis summary>"
  },
  "stage2_reframe": {
    "original_problem": "<stated problem>",
    "inverted_outcome": "<what would break success>",
    "second_order_causes": ["..."],
    "reframed_problem": "<improved problem statement>",
    "action_items": ["..."]
  },
  "gate_readiness": "READY|NEEDS_WORK|NOT_READY",
  "final_recommendation": "<list|rework|discard>"
}
```

## Quality Gate

- [ ] Stage 1 produces at least 3 failure modes AND 3 trust risks
- [ ] Stage 2 runs only if Stage 1 yields PASS or REVIEW
- [ ] Reframed problem differs from original problem
- [ ] Action items are concrete and actionable
- [ ] Final gate_readiness is specific and accurate

## Why This Composition Is Novel

Neither ingredient alone prepares a skill for gate submission:
- `chain_verifier_recipe` tells you IF the skill is trustworthy, but not WHY its problem definition might be wrong
- `lens_second_order_inversion` reframes problems, but doesn't validate quality

This pipeline chains them: verify first → reframe the verified skill's problem → return a gate-ready artifact. Different output than either ingredient alone.

## Usage

```
1. Read crafted/chain_verifier_recipe.md
2. Apply Stage 1 to your candidate skill
3. If verdict is PASS or REVIEW, read crafted/lens_second_order_inversion.md
4. Apply Stage 2 to the skill's stated problem
5. Combine outputs in Stage 3 synthesis
6. Use final_recommendation to decide: list, rework, or discard
```
