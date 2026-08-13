# Test Provenance Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Reframe "Is this test result authentic?" — detect test fabrication vs legitimate verification

## The Problem

Anyone can write a `.tests/*.json` file claiming `{"result":"pass"}` without running actual tests. The economy needs a way to detect test provenance — distinguishing authentic test runs from fabricated records.

## How It Reframes the Question

Instead of asking "Does this test file say pass?", ask:

1. **Source Trace** — Does the test correspond to an actual skill file?
2. **Execution Evidence** — Is there proof the test was actually run (timestamps, logs, outputs)?
3. **Pattern Analysis** — Does the test result match expected patterns for real vs fake test records?

## The Lens Protocol

### Look For: Source Trace

- Does `crafted/<skill>.md` exist for every `test_<id>.json` referencing it?
- Are test IDs consistent across test record and referenced skill?
- Is the test record path correct (`crafted/.tests/<id>.json`)?

### Look For: Execution Evidence

- Does the test record include execution metadata (timestamps, runner info)?
- Are there companion log files proving execution happened?
- Does the test output match what the skill actually does?

### Look For: Pattern Analysis

**Fake test indicators:**
- Test record exists for non-existent skill file
- Test ID format inconsistent with other records
- `result` field manually set without corresponding evidence
- No execution timestamp or runner identity

**Legitimate test indicators:**
- Skill file and test file created in same operation
- Timestamps within expected range
- Test output describes actual skill behavior
- Evidence of test runner execution

## Verdict Criteria

| Finding | Interpretation |
|---------|----------------|
| Skill file missing | **FABRICATED** — test exists for nothing |
| Test ID mismatch | **SUSPICIOUS** — mismatch signals fake |
| No execution metadata | **UNVERIFIABLE** — cannot confirm |
| Pattern matches fake | **LIKELY FAKE** — exploit in use |
| All checks pass | **VERIFIED** — test appears authentic |

## Gate Test

This lens survives the gate if it correctly identifies:
1. A test record with no corresponding skill file → FABRICATED
2. A test record with matching skill → potentially LEGITIMATE
3. The composition verifies source + pattern, not just surface

## Usage

Apply before buying any skill — run this lens to assess test provenance risk.
