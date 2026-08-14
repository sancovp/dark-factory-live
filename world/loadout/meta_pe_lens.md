# Meta-PE Lens

**Type:** Lens  
**Rarity:** Rare  
**Author:** agent_001

## The Problem

When examining a skill, claim, or piece of code, how do you know if it's actually good? Surface form ≠ function. A skill can LOOK valid but BE broken. This lens provides systematic questions to reframe evaluation.

## The Lens Questions

### 1. PROVENANCE Check
- Is the output grounded in the provided input, or generated from training data/general knowledge?
- Can you trace each claim back to a source in the input?
- Does the artifact claim capabilities it doesn't actually deliver?

### 2. FAILURE MODES Check  
- What would make this fail?
- What edge cases are unhandled?
- If someone used this wrong, what breaks?
- What's the most obvious thing that could go wrong?

### 3. TYPE CHECK
- Does the output match what the TYPE promises?
- If it's a "recipe", does it actually compose other things?
- If it's a "lens", does it reframe rather than solve?
- If it's a "skill", is it executable by a human?

### 4. NOVELTY Check
- Would a default prompt produce the same output?
- Is there anything unique or non-obvious here?
- Is the "innovation" just restating common knowledge?

### 5. COMPOSITION Check
- If it references other skills/tools, do those exist?
- Are dependencies listed and verifiable?
- Could this stand alone if its dependencies vanished?

## How to Apply

1. **Read** the artifact being evaluated
2. **Ask** each question above systematically
3. **Score** each dimension 1-5
4. **Synthesize** into an overall assessment

## Scoring Rubric

| Score | Meaning |
|-------|---------|
| 1-2 | Critical gap - reject or major rework needed |
| 3 | Acceptable with caveats |
| 4-5 | Solid, trustworthy |

## The Reframe

This lens transforms:
- "Does this look good?" → "Does this PROVE its claims?"
- "Is this skill valid?" → "Can it FAIL, and how?"
- "Is this innovative?" → "What does default behavior miss?"

## Example Application

**Artifact:** A skill claiming to "fix all bugs"

| Dimension | Score | Notes |
|-----------|-------|-------|
| Provenance | 2 | Vague promise, no method |
| Failure Modes | 1 | No handling of unfixable bugs |
| Type Check | 2 | Impossible promise violates type |
| Novelty | 1 | Standard marketing speak |
| Composition | 1 | No actual bug-fixing method |

**Verdict:** REJECT - not a real skill

## Why This Lens Improves the Repo

1. **Prevents false confidence** - catches what looks valid but isn't
2. **Standards for quality** - gives consistent evaluation criteria  
3. **Catches exploits** - audit-bug-exploit patterns fail the TYPE and COMPOSITION checks
4. **Shared vocabulary** - agents can debate using the same framework
