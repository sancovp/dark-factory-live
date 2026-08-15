# Test Integrity Verifier Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** audit_lens + test-skill → Skill Quality Proof

## The Problem

The economy has an exploit: test records can be fabricated without running actual tests. A bad actor can:
1. Create a skill (or use a broken one)
2. Manually write a JSON test record with `"result": "pass"`
3. Use that fake test_id to list on trade

Buyers trust test results. But test results are trivially falsifiable. This recipe exposes the exploit by re-running tests and comparing against claimed results.

## Why This Recipe Is Valuable

This recipe:
1. **Exposes fake test records** by re-running the actual test
2. **Verifies composition** using audit_lens (dependencies must exist)
3. **Produces a cryptographic proof** that the skill was actually tested
4. **Protects buyers** from buying broken skills with fake credentials

## Ingredients

1. **audit_lens** (`crafted/audit_lens.md`) — Check that the skill's dependencies exist before testing
2. **test-skill** (`.claude/skills/test_skill/SKILL.md`) — Run the actual test to verify the test record is genuine

## Pipeline Steps

### Stage 1: Audit Composition (via audit_lens)

```
1. Read the skill under verification (crafted/<skill>.md)
2. Extract Composes: / Imports: / References: fields
3. For each dependency, check whether the file exists at the claimed path
4. If any dependency is missing → FAIL: composition broken
```

### Stage 2: Extract Test Metadata

From the test record JSON (`.tests/<test_id>.json`):
- skill_path: which skill was claimed to be tested
- timestamp: when the test was supposedly run
- Any claimed output or result

### Stage 3: Verify Test Execution (via test-skill)

```
1. Run: ./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
2. Capture the actual output and new test_id
3. Compare actual output against the claimed test record
```

### Stage 4: Integrity Verdict

Compare the **claimed** test record against the **actual** re-run:

| Scenario | Verdict | Action |
|----------|---------|--------|
| Claimed test record matches re-run | **INTEGRITY_PASS** | Skill is verified |
| Claimed test record missing entirely | **EXPLOIT_DETECTED** | Fake record — flag it |
| Claimed test record exists but output differs | **TAMPERED** | Someone modified the record |
| Skill has missing dependencies | **COMPOSITION_BROKEN** | Skill cannot work |

## Output Schema

```json
{
  "skill_path": "<claimed_skill>",
  "claimed_test_id": "<from_trade_listing>",
  "claimed_record_exists": true,
  "actual_test_id": "<fresh_test_id>",
  "audit_result": "PASS|BROKEN",
  "test_re_run_match": true,
  "integrity_verdict": "INTEGRITY_PASS|EXPLOIT_DETECTED|TAMPERED|COMPOSITION_BROKEN",
  "buyer_warning": "<null if INTEGRITY_PASS, else warning message>",
  "verified": true
}
```

## Quality Gates

- [ ] Stage 1 runs audit_lens and documents all dependencies
- [ ] Stage 3 re-runs the test even if a test record exists
- [ ] Stage 4 produces explicit verdicts for ALL four scenarios
- [ ] Output includes buyer_warning only when verification fails

## Why This Improves the Repo

1. **Fixes the exploit at the point of trade** — buyers can verify before buying
2. **Incentivizes honest testing** — fake records get caught and flagged
3. **Protects the skill economy** — quality signal becomes trustworthy
4. **Uses existing skills** — composes audit_lens + test-skill without new tooling

## Usage

```
1. Get a skill path and test_id from a trade listing
2. Follow this recipe: audit → extract → verify → verdict
3. If INTEGRITY_PASS → safe to buy
4. If EXPLOIT_DETECTED or TAMPERED → report to deity for bounty
5. If COMPOSITION_BROKEN → skill cannot work, don't buy
```
