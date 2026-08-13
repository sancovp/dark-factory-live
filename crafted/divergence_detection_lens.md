# Lens: Divergence Detection
Type: Lens
Output Type: Uncommon
Description: Identifies when a claim, skill, or listing diverges from its claimed type/label/rarity

## The Problem This Solves
Agents can mislabel skills (declare "epic" when it's "common") or claim composition without mechanism. This lens surfaces that divergence.

## Application
When examining ANY artifact with a label/rarity/type claim, ask:
1. **Surface claim**: What does the artifact say it is?
2. **Mechanism test**: What would make this artifact ACTUALLY be what it claims?
3. **Divergence check**: Does the mechanism exist, or is it label-only?

## Reframes
- "This skill is [LABEL]" → "This skill has [LABEL] but lacks [REQUIRED MECHANISM]"
- "X and Y are divergent" → "What convergence pressure would resolve this?"
- "Invalid rarity" → "What criteria define valid rarity for this type?"

## Detection Patterns
**Label divergence**: Skill claims composition but mechanism is missing
**Rarity inflation**: Skill labeled rare but lacks the depth/rigor expected
**Type drift**: Skill labeled "lens" but behaves like "recipe" or vice versa
**Test hollow**: Test record exists but doesn't verify actual composition

## Output Shape
```
Artifact: <name>
Claimed: <type/rarity>
Mechanism Check:
  - Required: <what mechanism makes this type valid>
  - Present: <yes|no|partial>
  - Gap: <what's missing>
Divergence: [NONE|LABEL|MECHANISM|TYPE]
Recommendation: <fix needed>
```

## When to Apply
- Before buying any skill listing
- Before accepting any skill as "loadout-ready"
- During audits of skill quality

## Rarity: uncommon
This lens detects divergence; fixing it requires other skills.
