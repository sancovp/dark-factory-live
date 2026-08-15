# Artifact Proof Lens

## Type
Lens

## Rarity
uncommon

## What It Does
Reframes skill evaluation from "what does the seller claim?" to "what artifact evidence exists?". Shifts the question from trust to verification.

## The Lens Shift
**Before:** "Is this skill rare?" → Trust the seller's claim
**After:** "Can I PROVE this skill is rare?" → Demand artifact evidence

## Input
A skill path or listing_id claiming a specific rarity

## Questions This Lens Asks

1. **Test Execution Proof**: Does a test record exist AND can it be traced back to actual test.sh invocation?
   - Red flag: JSON exists, no execution trace, format anomalies

2. **Composition Evidence**: If claiming rare (complex), which specific skills does it compose?
   - Red flag: "complex composition" claim with no named dependencies

3. **Novelty Test**: Does the skill produce different output than a default prompt would?
   - Red flag: Template with fancy name, same output as bare instructions

4. **Tier Match**: Does claimed rarity match the artifact criteria?
   | Claimed | Minimum Evidence Required |
   |---------|--------------------------|
   | common | Valid skill file with type label |
   | uncommon | Test pass + no exploit flags |
   | rare | Novel approach OR complex composition OR edge case handling |
   | epic | Original contribution AND proven effectiveness |

## Output
```json
{
  "skill_path": "<path>",
  "claimed_rarity": "<rarity>",
  "artifact_evidence": ["list of proofs found"],
  "gaps": ["list of missing proofs"],
  "verified": true/false
}
```

## Usage
Before buying any skill, run this lens on the listing. If verified=false, either challenge the listing or skip.

## Composition
This lens composes:
- test-exploit-detection logic (checks for fabricated test records)
- rarity tier criteria (enforces minimum evidence per tier)
