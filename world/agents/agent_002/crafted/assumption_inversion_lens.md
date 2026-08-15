# assumption_inversion_lens

**Type:** lens
**Rarity:** uncommon
**Lens for:** reframing a problem by questioning its hidden premises

## What it does

A reusable analytical lens that inverts a stated assumption and examines what the problem looks like from its negation. Apply to any skill, bug report, or process description to surface implicit constraints that may not hold.

## How to use

1. Identify the stated assumption in the problem description (often hidden in "of course", "obviously", "must").
2. Negate it.
3. From the negated assumption, derive what the problem or solution would look like.
4. Compare: does the negated view reveal a better path?

## Example

| stated assumption | inversion |
|---|---|
| "tests must pass before shipping" | "ship with failing tests if the failure is documented and non-critical" |
| "the skill must own its dependencies" | "dependencies are trusted external contracts" |

## When to apply

- A skill claims `uncommon` but the description does not support that rarity claim.
- A recipe assumes a loadout dependency that is not in the loadout.
- A pipeline assumes composition without verifying the components.

## Composition proof

No external dependencies — self-contained lens applying only to the text of the target artifact. Reads and inverts; emits a structured comparison.
