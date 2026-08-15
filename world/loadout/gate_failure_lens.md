# Lens: Gate Failure Lens

**Type:** Lens
**Rarity:** Uncommon
**Reframes:** Any skill → "How would this fail the gate test?"

## What This Lens Does

Shifts analytical perspective from "what does this skill do?" to "what specific gate criteria would this skill fail, and how?" The gate is the factory's test_d71017677b56 and related CI checks. This lens maps any skill against concrete gate criteria to surface pass blockers before they cause a revert.

## The Lens Shift

**Before:** "Does this skill solve the stated problem?" → WRONG QUESTION  
**After:** "Would this skill pass the gate test? What would it fail on?" → RIGHT QUESTION

## Gate Criteria Reference

The gate tests:
1. **Composition proof** — skill's referenced dependencies must exist in loadout
2. **Output schema** — skill must produce a documented output format
3. **Test coverage** — skill must have a corresponding .tests/ record
4. **No revert signals** — skill must not trigger known revert patterns

## The Lens Questions

For any skill under review, ask these five questions:

### Q1: Dependency Gate
- What skills does this skill reference (import, link, or name)?
- Do those referenced skills exist in the loadout directory?
- **Failure signal:** any reference not in loadout = instant revert at composition check

### Q2: Schema Gate
- Does this skill declare an input schema?
- Does this skill declare an output schema?
- **Failure signal:** no schema = gate cannot verify correct invocation

### Q3: Test Coverage Gate
- Is there a .tests/ record for this skill?
- Does the test_id in the record match the skill's snake_case name?
- **Failure signal:** orphaned test or mismatched ID = no proof of execution

### Q4: Revert Pattern Gate
- Does this skill contain any known revert-triggering patterns?
  - Circular imports (A imports B imports A)
  - Missing error handling for edge cases
  - Hardcoded paths that break on different agents
- **Failure signal:** any revert pattern = fitness drops to 0

### Q5: Gate Convergence Risk
- Is this skill a duplicate or near-duplicate of an existing skill?
- Do other skills in loadout do the exact same thing?
- **Failure signal:** zero marginal value = recipe lens marks as redundant, gate may reject

## Output Format

```markdown
## Gate Failure Analysis for [skill_name]

### Dependency Gate: [PASS/FAIL]
  - References: [list]
  - Unresolved: [list or "none"]

### Schema Gate: [PASS/FAIL]
  - Input declared: [yes/no]
  - Output declared: [yes/no]

### Test Coverage Gate: [PASS/FAIL]
  - Test record exists: [yes/no]
  - Test ID matches: [yes/no]

### Revert Pattern Gate: [PASS/FAIL]
  - [list of detected patterns or "none"]

### Convergence Gate: [PASS/FAIL]
  - Redundancy score: [0-10]
  - [reason if redundant]

### Gate Pass Probability: [X]%
### Primary Failure Modes: [top 2 reasons]
### Fix Priority: [which gate to fix first]
```

## Why This Lens Is Novel

Existing lenses (audit_lens, dependency_lens, convergence_lens, adversarial_lens) all address different analytical angles. This lens is specifically scoped to the gate test — it applies the exact criteria that the CI/CD gate uses to determine pass/fail. No existing lens explicitly maps skills against the gate's own evaluation rubric. This is the lens the gate reviewer would run.

## Composition Dependence

None — this lens is self-contained and can be applied to any skill without external dependencies.

## Usage

1. Identify the skill under review
2. Apply the five gate questions
3. Read the skill markdown and loadout to answer each question
4. Compute Gate Pass Probability
5. If FAIL, prioritize fixes by gate criterion
