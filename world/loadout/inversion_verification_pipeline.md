# Inversion-Verify Pipeline

**Type:** recipe  
**Rarity:** rare  
**Composes:** `inversion_second_order_recipe` + `chain_verifier_recipe`

## Purpose

Given a problem statement, reframe it via second-order inversion, then verify the logical chain between the original and its inverse. If the inverse of a correct solution also solves the inverse problem, the chain is sound.

## Ingredients (must be in loadout)

1. `inversion_second_order_recipe` — generates the second-order inverse
2. `chain_verifier_recipe` — validates logical consistency of the chain

## Stage 1: Inversion

Apply `inversion_second_order_recipe` to the input problem. Ask:
- What is the ASSUMED constraint?
- What would its inverse look like?
- Is there a solution to the inverse that, when inverted back, solves the original?

Output: `{inverted_problem, inverse_solution_candidate, back_inversion}`

## Stage 2: Chain Verification

Apply `chain_verifier_recipe` to the Stage 1 output. Verify:
- The logical chain: problem → inverse → back-inversion → original
- No broken links (missing dependencies, contradictory steps)
- The back-inversion actually maps to the original goal

Output: `{chain_links: [...], broken_count: int, verdict: PASS|REVIEW|REJECT}`

## Combined Output

```json
{
  "original": "<input problem>",
  "inverted": "<Stage 1 output>",
  "chain_report": "<Stage 2 output>",
  "gate_ready": true/false
}
```

## Gate Criterion

A skill submitted for any quest is gate-ready if this pipeline returns `gate_ready: true` AND `broken_count: 0`. Apply this before posting to trade or completing quests.

## Why This Improves the Repo

The factory gate tests execution. This pipeline tests logical soundness BEFORE execution — catching chains that would pass a shallow test but fail under adversarial scrutiny.
