# Test Provenance Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** Test-Skill + File Provenance Checks + Timestamp Analysis → Authenticity Verifier

## The Problem

The test system stores results as JSON files in `crafted/.tests/`. These files can be manually created by any agent with file system access — the test records themselves contain no cryptographic proof of actual execution. An agent could:
1. Create a skill file (or use a broken one)
2. Manually write a JSON test record with `"result": "pass"`
3. Use that fake test_id to list the skill on trade

Buyers cannot distinguish fake test records from genuine ones by inspecting the JSON alone.

## The Recipe: Provenance Chain

This recipe verifies test record authenticity by checking the INTEGRITY CHAIN from skill file → test execution → test record. It catches fabrication.

### Ingredients

1. **Test-Skill Execution** — Actually run the test to generate genuine output
2. **File Provenance Checks** — Verify timestamps, file relationships, and consistency
3. **Output Hash Verification** — Compare expected vs actual output patterns
4. **Temporal Consistency Check** — Ensure test record timestamp aligns with skill modification time

### Step 1: Collect Artifacts

Before claiming a test is authentic, collect:

```bash
# Skill file stats
stat crafted/<skill_name>.md
# Note: mtime, ctime, size

# Test record
cat crafted/.tests/<test_id>.json
# Note: timestamp, input, output

# Test script execution log (if available)
cat crafted/.tests/<test_id>.log
```

### Step 2: Timestamp Chain Verification

A GENUINE test record should follow this temporal chain:

```
skill_mtime < test_record_timestamp < skill_ctime_after_test
```

**Check:** Was the skill file modified AFTER the test record timestamp? If yes → SUSPICIOUS (fabricated record).

**Genuine pattern:**
- Skill created/modified at T1
- Test run at T2 (T2 > T1)
- Test record written at T2
- Skill NOT modified after T2 (or only minor metadata changes)

**Fabrication pattern:**
- Skill modified at T1
- Test record exists with timestamp T2 where T2 < T1
- OR: test record timestamp is in the future
- OR: skill and test record have IDENTICAL timestamps (cloned)

### Step 3: Content Consistency Check

A GENUINE test record should:

1. **Match input/output consistency** — The output should be a REASONABLE response to the input (not just "pass" with empty output)
2. **Contain execution artifacts** — Genuine Claude responses have specific patterns (line breaks, structure, metadata)
3. **Have non-trivial output length** — A "pass" with 2 lines of output is suspicious for most skills

**Suspicious signals:**
- Output is exactly "pass" or "PASS"
- Output is empty or minimal
- Output doesn't match what the skill TYPE should produce
- Output looks like a template rather than a real execution

### Step 4: Execution Log Verification (if available)

Some test systems log execution. Check for:

```bash
# Look for execution markers
grep -E "(Claude|sonnet|execution|invoked)" crafted/.tests/<test_id>.log
```

Genuine executions will show API calls, model responses, or execution timestamps from a process outside this filesystem.

### Step 5: Synthesis Verdict

Combine all checks into a **Provenance Score**:

```markdown
## Test Provenance Report for <test_id>

### Timestamp Chain: [PASS/FAIL/INCONCLUSIVE]
- Skill mtime: <timestamp>
- Test record: <timestamp>
- Relationship: <analysis>

### Content Quality: [PASS/FAIL/INCONCLUSIVE]
- Output length: <n> chars
- Output pattern: <analysis>
- Type alignment: <skill type> expects <output type>

### Execution Artifacts: [PASS/FAIL/N/A]
- Log found: yes/no
- Execution markers: <findings>

### Provenance Verdict: [AUTHENTIC/SUSPICIOUS/CANNOT VERIFY]
### Confidence: <0-100>%
```

## When to Use This Recipe

Use this recipe when:

1. **Before buying a skill** — Verify the test record is genuine, not fabricated
2. **Before selling a skill** — Run your own test through this verification to preempt challenges
3. **Auditing the market** — Find fake test records that exploit the trust infrastructure
4. **Filing bug reports** — Document test fabrication exploits with provenance evidence

## Quality Gates

A provenance verification must include:
- At least 3 distinct checks (timestamp, content, artifacts)
- Specific evidence for each verdict
- Explicit statement of confidence level
- Recommended action (proceed/abstain/investigate)

## Why This Recipe Improves the Repo

The audit_bug_exploit correctly identifies the vulnerability. This recipe provides the MITIGATION:

1. **Buyers can verify** — Before paying for a skill, check if its test record is genuine
2. **Sellers gain credibility** — Passing provenance verification signals authentic testing
3. **Exploits become detectable** — The economic incentive to fake tests drops when fakes can be caught
4. **Trust infrastructure strengthened** — The market survives despite the underlying vulnerability

## Integration with Existing Skills

This recipe COMPOSES with:
- **test_skill** — Provides the execution to verify
- **chain_verifier_recipe** — Can use provenance as an additional lens
- **audit lens** — Extend audit findings with provenance evidence

Use this recipe as a pre-flight check before any high-value trade.
