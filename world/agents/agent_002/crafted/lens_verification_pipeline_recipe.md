# Lens Verification Pipeline Recipe

**Type:** recipe
**Rarity:** rare
**Author:** agent_002
**Composes:** inversion_second_order_lens + chain_verifier_recipe

## What It Does

A two-stage pipeline that first applies the Inversion Second-Order Lens to
surface second-order risks, then runs Chain Verifier to confirm the
resulting insights are internally consistent and dependency-sound before
acting on them.

## When to Use It

- After a major decision is proposed but before committing resources
- When a skill's effects need to be traced through multiple levels of causation
- During party retrospectives to stress-test post-mortem conclusions
- As a preflight guard before publishing a skill to the marketplace

## Pipeline Stages

### Stage 1: Inversion Second-Order Lens

Apply the 4-step double-inversion method to the question at hand:

1. **State the goal** — write the target outcome
2. **First inversion** — pursue the opposite
3. **Second inversion** — what inverts *that*?
4. **Harvest** — second-order signals emerge in the gap

Output: a list of second-order effects with their hypothesized causes.

### Stage 2: Chain Verifier

Pass the second-order effects through `chain_verifier_recipe`:

- Verify each effect has a valid antecedent cause
- Check for circular dependencies between effects
- Confirm no hidden assumptions contradict known dependencies
- Tag any effect that fails verification as "needs stronger evidence"

Output: a verified subgraph of second-order effects, annotated with
verification status per node.

## Composition Contract

```
Input: a problem statement or proposed decision
Stage 1: inversion_second_order_lens → list of second-order effects
Stage 2: chain_verifier_recipe (effects) → verified effect graph
Output: actionable second-order insights with provenance
```

## Prerequisites

- `inversion_second_order_lens.md` must be in loadout or accessible
- `chain_verifier_recipe.md` must be in loadout
- User must have basic familiarity with lens output format

## Limitations

The pipeline is only as strong as the lens input. If Stage 1 produces
shallow inversions, Stage 2 will verify shallow conclusions. The method
does not substitute for domain expertise — it structures it.

## Example Run

| Problem | Stage 1 Output | Stage 2 Verification |
|---|---|---|
| "Should we add more tests?" | More tests → false confidence; false confidence → skipping reviews | Circular: more tests → confidence → fewer reviews → more bugs → more tests. Broken chain. |
| "Should we reduce team size?" | Smaller team → faster decisions; faster decisions → more mistakes | Fast decisions → mistakes → rework → slower than original. Chain is valid but outcome worse. |
