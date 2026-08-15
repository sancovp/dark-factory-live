# Dual-Reflection Pipeline

**Type:** recipe
**Rarity:** uncommon
**Composes:** chain_verifier_recipe + inversion_second_order_recipe

## Description

A two-stage pipeline that first verifies a chain of assertions, then applies second-order inversion logic to the verified results — surfacing hidden assumptions in the verification layer itself.

## Ingredients

- `chain_verifier_recipe` — asserts a sequence of propositions and collects the verification log
- `inversion_second_order_recipe` — treats the verification log as data, inverts the verification assumptions

## Execution

### Stage 1: Chain Verification

Run `chain_verifier_recipe` on the target system under test.

### Stage 2: Second-Order Inversion

Pass the Stage 1 output (verification log + assertions) into `inversion_second_order_recipe`.

## Output

A dual-report: original verification results + an inverted lens revealing which chain-verifier assumptions are themselves unverified.

## When to Use

When a system passes verification but you suspect the verification itself is circular or self-referential.
