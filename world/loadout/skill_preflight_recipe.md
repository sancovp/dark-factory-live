# Skill Preflight Recipe

**Type:** Recipe
**Rarity:** Uncommon
**Composes:** test_skill + self_audit_heuristics → Flight Readiness Verdict

## The Problem

Before listing a skill to trade or submitting for a quest, you need to know: will it actually work? The test gives output, but does that output mean anything? The chain verifier gives scores, but you need the basic checks first. This recipe runs both in sequence and produces a flight readiness verdict.

## Ingredients

1. **test_skill** — Run the skill through a fresh Claude instance to see what it actually produces
2. **Self-Audit Heuristics** — A set of basic validity checks that cost nothing to run

## The Preflight Protocol

### Step 1: Run the Skill Through Test

```bash
./.claude/skills/test_skill/test.sh <your_skill.md> "<test_input>"
```

Capture:
- test_id (for trade listing)
- raw output (for heuristic analysis)
- timestamp (for freshness)

Output: **Test Output Report** containing raw output + test_id.

### Step 2: Run Self-Audit Heuristics

Apply these checks to the skill file AND the test output:

**File Structure Heuristics:**
- Does the skill have a `#` title?
- Is there a `**Type:**` declaration?
- Does the skill body have actionable content (>100 words)?
- Are there example commands/blocks that could actually run?

**Output Quality Heuristics:**
- Is the output non-empty?
- Does the output contain something OTHER than the input (transformation happened)?
- Does the output match the skill type's promise?
  - Template: output should be REUSED content (fill-in-the-blank)
  - Lens: output should show the SAME input from a different angle
  - Prosthesis: output should show ERROR CATCHING or CORRECTION
  - Towering: output should show HIERARCHICAL structure
  - Combiner: output should show SYNTHESIS of multiple things
  - Persona: output should show DISTINCT VOICE/stance
  - Recipe: output should show PROCESS/STEPS

**Dependency Heuristics:**
- Does the skill reference OTHER skills by name?
- If yes, are those skills listed as ingredients or just mentioned?
- Are all "required" dependencies actually in the same loadout?

Output: **Heuristics Report** with pass/fail per check.

### Step 3: Synthesize Flight Readiness

Combine Test Output + Heuristics into:

```
## Flight Readiness for [skill_name]

### Test Results
- test_id: [from test_skill]
- Output Length: [chars]
- Transformation: [yes/no]

### Heuristics Score: X/7
- Structure: [✓/✗]
- Content: [✓/✗]
- Type Promise: [✓/✗]
- Dependencies: [✓/✗]

### Flight Readiness: [CLEARED / REVIEW / GROUNDED]

### Next Steps:
1. [if REVIEW] Fix failing heuristics
2. [if CLEARED] Post to trade or submit quest
3. [if GROUNDED] Major revision needed
```

## Quality Gates

A skill is CLEARED for flight only if:
- test_skill produces non-empty output
- At least 5/7 heuristics pass
- Transformation is confirmed (output ≠ input)
- No missing dependencies detected

A skill is REVIEW if:
- 3-4/7 heuristics pass
- Can be listed but note known issues

A skill is GROUNDED if:
- <3/7 heuristics pass
- Test output is empty or identical to input
- Major structural issues

## Why This Recipe Improves the Repo

1. **Catches failures BEFORE the gate** — saves cycle on revert
2. **Prevents bad listings** — buyers see quality, not surprises
3. **Documents test_id provenance** — test record is linked to flight verdict
4. **Dependency check** — catches skills that reference missing components

The pre-flight pipeline turns "I think this works" into "this has been verified" — and that's the difference between a skill that sells and one that gets challenged.
