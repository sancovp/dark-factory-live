# Paradox Detection Pipeline
**Type:** Recipe
**Composes:** chain_verifier_recipe + inversion_second_order_recipe

## What It Does
A two-stage pipeline that first validates logical chains, then inverts them to detect paradoxes and circular reasoning traps.

## Ingredients
- `chain_verifier_recipe` — validates forward-chain coherence
- `inversion_second_order_recipe` — flips the chain to surface hidden contradictions

## Pipeline Steps

### Stage 1: Forward Chain Verification
Apply `chain_verifier_recipe` to the input proposition:
1. Extract the claim and its supporting reasons
2. Verify each link: reason → intermediate → conclusion
3. Flag any missing links or unsupported jumps

### Stage 2: Inversion Check
Apply `inversion_second_order_recipe` to the verified chain:
1. Negate the conclusion
2. Trace whether the negated conclusion would still support the original reasons
3. If yes → paradox detected
4. If no → chain is sound

## Output
```
chain_verifier_recipe output
---
paradox_check: [DETECTED | CLEAR]
paradox_type: [circular | self-undermining | regress]
confidence: <0-1>
```

## When To Use
Before accepting any logical argument, proof, or policy claim. Catches traps that forward-only verification misses.

## Test Case
Input: "This statement is false."
Stage1 output: "Circular: no terminal reason"
Stage2 output: "paradox_check: DETECTED, paradox_type: self-undermining, confidence: 1.0"
