# Gate Predictor Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Predict whether a skill will pass the test gate before submission

## The Lens

Before you submit a skill to the gate, ask: "Will this pass?"

The Gate Predictor Lens forces you to see your skill through the gate's judgment criteria, not your own satisfaction. Most agents test their skills as they WISH them to work — not as the gate WILL test them.

## Questions to Apply

### 1. Structural Check
- Does the skill have required metadata fields (name, type, rarity, description)?
- Is the file path valid and the format correct?
- Does the skill reference dependencies that actually exist?

### 2. Output Check
- Does the skill produce non-empty output on typical inputs?
- Does the output differ from the input?
- Are there obvious failure modes the gate would catch?

### 3. Rarity Claim Check
- Is the claimed rarity justified by the actual complexity/uniqueness?
- Would an objective observer agree with this rarity?
- Could a simpler skill claim the same rarity?

### 4. Test Record Check
- Is there a corresponding test record in `.tests/`?
- Does the test_id format match expected patterns?
- Is the test result credible (not obviously fabricated)?

## The Prediction Protocol

For each question, answer:
- **YES** = point toward gate pass
- **NO** = point toward gate fail  
- **UNSURE** = flag for preflight verification

### Prediction Formula

Gate Pass Probability = (Structural_YES + Output_YES + Rarity_YES + Test_YES) / 4 * 100%

### Interpretation

| Score | Prediction | Action |
|-------|-----------|--------|
| 100% | CONFIDENT PASS | Submit directly |
| 75% | LIKELY PASS | Fix UNSURE items first |
| 50% | UNCERTAIN | Run preflight before submit |
| 25% | LIKELY FAIL | Revise before submitting |
| 0% | CONFIDENT FAIL | Don't submit — rebuild |

## Why This Lens Improves the Repo

The standing rules document that fitness can drop despite stages passing — skills pass internal checks but fail the gate. This lens catches that failure mode BEFORE submission.
