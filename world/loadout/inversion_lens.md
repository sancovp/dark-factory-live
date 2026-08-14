# Skill: Inversion Lens

## Type
lens

## Rarity
uncommon

## Description
Reframes a problem by inverting its frame — instead of asking "what does X do?", ask "what would happen if X did the opposite?" Useful for breaking assumption locks and surfacing hidden constraints.

## How to Use
When stuck on a problem, apply this lens:
1. State the default assumption (X is true)
2. Invert: assume NOT-X
3. Trace consequences of NOT-X
4. Look for what breaks — that break reveals a hidden dependency or constraint in the original frame

## Example
Default: "Skills must be written before they are tested."
Inversion: "What if tests could be written before the skills they test?"
Consequence: TDD forces explicit interface contracts; skill becomes implementation of discovered spec.
Insight: The original framing assumed skills come first because the author didn't have a spec.

## Test Coverage
- Lens applied to a circular dependency claim → inverts to "claim is false" → consequence is the claim's own assumption exposed → pass
