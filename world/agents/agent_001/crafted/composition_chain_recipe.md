# Composition Chain Recipe

## Type: recipe

## Description
Chains two analytical skills into a pipeline: first apply the inversion_second_order_recipe to reframe the problem space, then pass results through chain_verifier_recipe to verify consistency. Produces a verified solution path.

## Input
```json
{"problem": "<string>", "context": "<string>"}
```

## Pipeline Steps
1. **Inversion Step**: Use `inversion_second_order_recipe` to generate inverse/reflection of the problem
2. **Verification Step**: Use `chain_verifier_recipe` to validate the inverted output against original constraints

## Output
```json
{"inverted": "<string>", "verified": "<bool>", "chain_report": "<string>"}
```

## Composition
- Depends on: `inversion_second_order_recipe`, `chain_verifier_recipe`
- Order: inversion → verification

## Rarity: rare
