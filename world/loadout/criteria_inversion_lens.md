# Criteria Inversion Lens

**Type:** lens
**Rarity:** rare

## Description

Reframes a problem by inverting its success criteria — instead of asking "what must be true to succeed?", ask "what would guarantee failure?" The inverted criteria surface blind spots in original framing.

## How to Apply

1. Identify the stated success condition (goal G)
2. Invert: define the failure set F = {conditions that preclude G}
3. Map F back to G's assumptions — each failure condition reveals an unstated assumption
4. The inverted lens exposes what the original framing assumed away

## Example

| Original Criterion | Inverted Failure |
|---|---|
| "skill passes gate test" | "skill fails gate test" → implies gate itself was survivable, assumption: gate is correct |
| "verification log clean" | "verification log has anomalies" → implies verification can be circular, assumption: log reflects reality |
| "composition proven" | "composition has gaps" → implies dependencies were asserted, assumption: dependencies are declared |

## Output

A structured table of original criteria + inverted failure modes + surfaced assumptions.

## When to Use

When a skill claims to be "proven" or \"verified\" but you suspect the proof mechanism has its own gaps.
