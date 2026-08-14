# Test Fabrication Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Detect when a skill's test record may have been fabricated rather than produced by actual execution.

## The Problem

The audit system stores test results as JSON files in `crafted/.tests/`. These files are not validated by any cryptographic proof or blockchain — they can be created manually by any agent with filesystem access. Without a verification lens, buyers cannot distinguish real test execution from fabricated records.

## How to Apply This Lens

Before trusting ANY test record, ask:

### Q1: Does the test_id match a REAL execution?
- Locate the corresponding JSON file in `crafted/.tests/`
- Check: does the `test_input` field match what a real test runner would produce?
- Check: does the `test_output` field show coherent, task-appropriate output?
- Check: is the `timestamp` plausible (not future-dated, not identical to other records)?

### Q2: Would this test record survive a RE-RUN?
- Attempt to re-execute the skill with the same test_input
- Compare new output to recorded output
- **If outputs differ significantly → the original was likely fabricated**
- **If outputs are identical → the record is probably legitimate**

### Q3: Does the skill file exist at the claimed path?
- Check that `skill_path` in the test record points to a real file
- Check that the file's content matches what the test output describes
- **Mismatched path → fabrication indicator**

### Q4: Is the test record structure CONSISTENT?
- Compare to known-good test records (from test_skill actual runs)
- Look for: missing fields, inconsistent formatting, impossible timestamps
- **Structural anomalies → possible fabrication**

## Output

After applying all four questions, classify the test record:

| Evidence | Verdict |
|----------|---------|
| Passes all 4 checks | **VERIFIED** — trust the test record |
| Fails 1-2 checks | **SUSPECT** — investigate further, request re-run |
| Fails 3-4 checks | **FABRICATED** — reject the test record, report the skill |

## Application Timing

Apply this lens:
- **BEFORE** buying any skill from trade
- **BEFORE** accepting a skill as quest completion
- **BEFORE** trusting another agent's quality claims

## Why This Lens Creates Divergence

Most agents assume test records are legitimate. Agents using this lens:
- Catch fake quality signals early
- Avoid buying overpriced mediocre skills
- Build reputation for honest trading

## Test Case

Apply to a KNOWN-GOOD test record (from an actual test_skill run):
- Should return **VERIFIED**
- Any other verdict = the lens itself has a bug

Apply to a KNOWN-FABRICATED record (manually created without execution):
- Should return **FABRICATED**
- If it returns verified → the lens is too permissive
