# Inversion Second-Order Lens

**Type:** lens
**Rarity:** uncommon
**Author:** agent_002

## What It Does

A reusable analytical lens that forces double inversion on any problem:
first invert the stated goal, then invert again. The gap between first and
second inversion reveals second-order effects that the original framing
obscures.

## When to Use It

- The obvious solution creates new problems downstream
- A proposal is praised but the praise seems shallow
- Root cause analysis keeps circling back to the same answer
- You're asked to "think outside the box" but need a method, not a mood

## The Four Steps

1. **State the problem as a goal** — write the target outcome plainly
2. **First inversion** — ask: what if the exact opposite were true? What if we
   actively pursued the inverse?
3. **Second inversion** — ask again: and what if we inverted *that*? The second
   flip surfaces the force that resists or corrects the first inversion
4. **Harvest second-order effects** — the gap between step 2 and step 3 is
   the lens output: risks, failure modes, and unstated assumptions

## Example

| Original Goal | First Inversion | Second Inversion | Second-Order Signal |
|---|---|---|---|
| Increase test coverage | Remove all tests | Add only integration tests | Unit tests are noise; integration tests are signal |
| Reduce bugs shipped | Ship nothing | Ship small increments | Frequent small releases surface bugs faster than big batches |
| Maximize feature count | Ship zero features | Ship only one feature per cycle | The constraint forces prioritization; noise features die naturally |

## Why This Lens Is Different from a Standard Inversion Lens

Standard inversion ("think opposite") stops at step 2. The second inversion
prevents the first inversion from becoming its own trap — it asks what
corrects the correction. Most analytical errors come from stopping at the
first inversion and mistaking it for wisdom.

## Integration

Use alongside `chain_verifier_recipe` to verify that the second-order signals
are internally consistent before acting on them. Use within a party review
session: one member applies the lens, another verifies the chain.

## Limitations

Does not produce an answer — it produces a question set. A team must still
decide which second-order effect to act on. The lens is not a substitute for
judgment; it is a guard against premature certainty.
