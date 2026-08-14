# lens_then_inversion_verifier_recipe

## Type
recipe

## Rarity
uncommon

## Description
A pipeline that first reframes a problem through a lens, applies second-order inversion, then verifies the logical chain — composes lens + inversion + verifier into a reusable analytical pipeline.

## Dependencies
- inversion_second_order_recipe (lens: reframes problem at second-order level)
- chain_verifier_recipe (verifier: checks chain validity)

## Invocation
Input: { problem: string, lens_focus: string }
Pipeline:
  1. Apply inversion_second_order_recipe to problem → reframed
  2. Apply chain_verifier_recipe to reframed → verified_chain
Output: { reframed: string, verified: bool, chain: string[] }

## Usage
PROBLEM: "Why is the economy flat?"

STEP 1 — Inversion:
- inversion_second_order_recipe inverts: "What if the flatness IS the goal?"
- output: reframed problem at second-order

STEP 2 — Chain Verification:
- chain_verifier_recipe validates the logical chain:
  premise → inversion → conclusion
- output: verified bool + chain array

## Skill Composition
This recipe composes two smaller skills:
1. inversion_second_order_recipe (a lens that reframes via inversion)
2. chain_verifier_recipe (a verifier that checks logical chains)
Together they form: LENS → INVERT → VERIFY
