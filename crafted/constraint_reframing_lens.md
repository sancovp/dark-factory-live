# skill: constraint_reframing_lens

## Type: lens

## What It Does
Shifts analysis from "what's wrong with X?" to "what constraints must X satisfy?" Problems that look like failures often reveal themselves as constraint violations. This lens systematically extracts constraints and tests whether the subject meets each one — converting vague "problems" into precise "violations."

## The Reframes
- "Why does X fail?" → "What constraint is X violating?"
- "How do I fix X?" → "Which constraint, if satisfied, resolves the failure?"
- "X and Y are different" → "X and Y satisfy different constraint subsets"

## Application Steps
1. **Identify the failure surface**: What observable symptom or bad outcome exists?
2. **Extract candidate constraints**: What must be true for this outcome NOT to occur? (2-4 constraints minimum)
3. **Classify each constraint**:
   - KNOWN MET: can verify the subject satisfies it
   - KNOWN VIOLATED: can verify the subject violates it  
   - UNKNOWN: cannot currently assess
4. **For KNOWN VIOLATED**: Which, if satisfied, would eliminate the failure?
5. **Reframe the problem**: "The root issue is violation of constraint C, not the symptom S."

## Input Triggers
- "X is broken/failing/problematic"
- "X doesn't work as expected"
- "X and Y behave differently" (constraint subset divergence)
- "How do I fix X?"

## Output Shape
- List of extracted constraints (with KNOWN/KNOWN_VIOLATED/UNKNOWN tags)
- The binding constraint (the one whose satisfaction would resolve the failure)
- Reframed problem statement in constraint language
- Action: satisfy the binding constraint

## Example
**Before:** "My pipeline keeps failing on edge cases."
**After:** "My pipeline fails when: (1) KNOWN MET: input is well-formed, (2) KNOWN VIOLATED: input exceeds 10k tokens, (3) UNKNOWN: non-ASCII characters present. The binding constraint is 'input length ≤ 10k tokens' — fix that, test the UNKNOWN, done."

## Rarity: rare
