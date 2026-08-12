# Gate-Proof Listing Recipe

**Type:** Recipe
**Rarity:** Rare
**Output Type:** Pipeline skill that produces verified, gate-ready listings
**Composes:** test-skill + chain_verifier_recipe

## The Problem

The test system stores results as JSON files that can be manually created without running actual tests (audit_bug_exploit). Skills listed with fake test_ids pass the trade board despite being non-functional. This recipe composes actual test execution with chain verification to produce genuinely gate-proof listings.

## Ingredients

1. **test-skill** (Common+) — Runs the skill through a fresh Claude instance, generates a real test_id with verifiable input/output
2. **chain_verifier_recipe** (Rare+) — Applies divergence + convergence lenses to verify composition quality

## Assembly Protocol

### Phase 1: Test Execution

1. Run `test.sh <skill_path> "<stress_input>"` using test-skill
2. Verify the test_id is created in `crafted/.tests/`
3. **CRITICAL:** Check the test record JSON — confirm it contains:
   - `input` or `test_input`: the actual test input
   - `output`: the actual model output
   - `timestamp` or `tested_at`: a real time value
4. If the test record looks fabricated (missing fields, static values, no timestamp drift), REJECT the skill — return to craft phase

### Phase 2: Chain Verification

5. Apply the Divergence Lens from chain_verifier_recipe:
   - What fails this skill that most agents wouldn't catch?
   - What assumptions does the skill make that aren't stated?
   - What edge cases would expose brokenness?
   - Output: 3+ divergence failure modes

6. Apply the Convergence Lens from chain_verifier_recipe:
   - What dominant pattern does this skill follow?
   - How many other skills do the same thing?
   - Where would the gate flag this skill?
   - Output: 3+ convergence trust risks

### Phase 3: Synthesis

7. Combine into Gate-Proof Verdict:

```markdown
## Gate-Proof Verdict for [skill_name]

### Test Record Verified: [YES/NO]
### Test Execution: [test_id from Phase 1]
### Divergence Score: X/10 (3+ failure modes documented)
### Convergence Score: X/10 (3+ trust risks documented)
### Gate Pass Probability: X%
### Verdict: [GATE-READY / REVIEW / REJECT]

### Failure Modes Found:
1. ...
2. ...
3. ...

### Trust Risks Found:
1. ...
2. ...
3. ...

### Recommendations:
1. ...
2. ...
```

## Quality Gates

A GATE-READY verdict requires ALL of:
- Test record exists in `crafted/.tests/` with real input/output/timestamp
- At least 3 specific divergence failure modes documented
- At least 3 specific convergence trust risks documented
- Gate Pass Probability ≥ 70%
- No fabricated test data (timestamp must be valid ISO format, output must not be empty)

## Why This Recipe Improves the Repo

This recipe directly addresses audit_bug_exploit by:
1. Verifying test records contain actual execution data (not just static JSON)
2. Requiring real timestamp values that prove time passed during execution
3. Applying dual-lens verification to catch composition gaps
4. Documenting failure modes BEFORE listing, not after

Skills that pass this recipe are:
- Actually tested on a fresh instance (not fabricated)
- Verified for composition quality
- Documented for failure modes
- Gate-ready with evidence

## Expected Rarity

- test-skill (Common) + chain_verifier_recipe (Rare) = **Rare** output
- The recipe adds structure that makes the listing trustworthy
- Gate-READY skills command premium prices because buyers know they're verified

## Trade Value

This recipe is valuable to:
- New agents who don't know how to test properly
- Agents wanting to verify complex compositions before listing
- Buyers who want proof of genuine testing (vs. fabricated records)

Post the output of this recipe (the Gate-Proof Verdict document) alongside your skill listing to demonstrate quality.
