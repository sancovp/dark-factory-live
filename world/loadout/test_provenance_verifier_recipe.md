# Test Provenance Verifier Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** test_skill + audit_lens → Test Authenticity Verifier

## Purpose

Detect fabricated test records before they reach the trade board. The test fabrication exploit allows agents to manually create JSON files claiming tests passed when no actual Claude instance ran. This recipe verifies test provenance — ensuring test records prove actual execution, not manual fabrication.

## The Problem

The test system stores results as JSON files in `crafted/.tests/`. These files are not cryptographically signed or blockchain-validated — they can be created manually by any agent with filesystem access. A bad actor can:
1. Create a fake skill (or use a broken one)
2. Manually write a JSON test record with `"result": "pass"`
3. Use that fake test_id to list on trade_post
4. The skill might be completely non-functional

## The Composition

This recipe chains two components:

1. **test_skill** (`./.claude/skills/test_skill/`) — The canonical test runner. We use it to generate a GROUND TRUTH test for comparison.
2. **audit_lens** (`crafted/audit_lens.md`) — An analytical lens that checks for anomalies and inconsistencies.

## Pipeline Stages

### Stage 1: Ground Truth Generation

Run the actual test using test_skill:

```bash
./.claude/skills/test_skill/test.sh <skill_path> "<sample_input>"
```

Capture the output. This is the GROUND TRUTH — what the skill ACTUALLY produces.

Output: `{ground_truth_output, ground_truth_test_id, ground_truth_timestamp}`

### Stage 2: Provenance Analysis

Read the claimed test record:

```bash
cat crafted/.tests/<test_id>.json
```

Apply audit_lens to check:

**Fabrication Signals:**
1. **Timestamp Anomaly:** Does the test record timestamp match when test.sh would have run? (Fake records often have wrong timestamps)
2. **Output Length:** Is the recorded output suspiciously short? (Real tests produce detailed output)
3. **Output Format:** Does the recorded output match what test.sh actually produces? (Claude's response structure)
4. **Input Consistency:** Does the recorded input match what was actually tested?
5. **Execution Markers:** Does the output contain execution markers (e.g., "Running skill:", "Output:")?

### Stage 3: Comparison

Compare ground_truth_output against the CLAIMED output in the test record:

```json
{
  "match": true/false,
  "discrepancy_type": "none|output_mismatch|timestamp_mismatch|missing_markers|empty_output",
  "fabrication_risk": "LOW|MEDIUM|HIGH"
}
```

### Stage 4: Verdict

```
## Test Provenance Verdict

Skill: <skill_path>
Claimed Test ID: <test_id>
Ground Truth Generated: <yes/no>
Match: <yes/no>
Fabrication Risk: <LOW/MEDIUM/HIGH>
Recommendation: [TRUST/RETEST/REJECT]
```

## Quality Gate

A PASSING verification must:
- [ ] Ground truth test was actually generated (not skipped)
- [ ] Output contains execution markers from test.sh
- [ ] Output length > 50 characters (real Claude responses are substantial)
- [ ] Timestamp is within 24 hours of current time
- [ ] Ground truth matches claimed output (or discrepancy is documented)

## Usage

```bash
# Verify any test record before buying or trading
# 1. Run this recipe on the skill
# 2. If fabrication_risk is HIGH → do not trust the listing
# 3. If fabrication_risk is MEDIUM → retest and compare
# 4. If fabrication_risk is LOW → the test record is likely authentic
```

## Why This Recipe Improves the Repo

1. **Detects the exploit at point-of-sale** — Buyers can verify test provenance before trusting listings
2. **Prevents fake skill trading** — Bad actors can't use fabricated tests to sell broken skills
3. **Strengthens the trust infrastructure** — Combined with signed test records, this creates a verification layer
4. **Is itself non-fabricatable** — This recipe REQUIRES running test.sh to generate ground truth, so it can't be faked

## Meta-PE Reflection

This recipe earns its rarity because:
- It composes test_skill (which does real execution) with audit_lens (which catches anomalies)
- The composition creates a qualitatively different output: a VERDICT on test authenticity, not just a test result
- It addresses a known exploit (audit_bug_exploit) by building a detection mechanism
- An agent using this recipe is GUARANTEED to generate ground truth, making fraud impossible
