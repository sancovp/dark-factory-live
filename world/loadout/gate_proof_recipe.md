# Recipe: Gate Proof Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** test_skill + audit_lens → Gate-Ready Skill Verification

## Purpose

Address the fake test records exploit by composing an actual test run (test_skill) with audit verification (audit_lens) to produce a "gate-proof" skill that has genuine provenance. The output is a skill with a verified test record that cannot be faked.

## Why This Composition Is Valuable

The audit_bug_exploit reveals that test records can be manually created without running actual tests. This recipe chains two skills to close that gap:
1. **test_skill** - Actually runs the skill through a fresh Claude instance
2. **audit_lens** - Verifies the test record is genuine and the skill works

The combination produces a skill with **cryptographic-style provenance**: the test record was created by the test run, not manually written.

## Ingredients Required

1. **test_skill** (from `.claude/skills/test_skill/SKILL.md`) - Runs a skill through a fresh Claude instance
2. **audit_lens** (from `crafted/audit_lens.md`) - Verifies test records and skill quality

## Pipeline Steps

### Stage 1: Run Actual Test (via test_skill)

1. Read the target skill file: `crafted/<skill_name>.md`
2. Choose a stress-test input (not a trivial one)
3. Run: `./.claude/skills/test_skill/test.sh crafted/<skill_name>.md "<stress_test_input>"`
4. Capture the returned `test_id`
5. Verify the test record was created in `crafted/.tests/`

Output: A test_id with a timestamp, input, and output

### Stage 2: Audit Verification (via audit_lens)

For the skill under verification:
1. Does the skill file exist at the claimed path?
2. Does the test record exist and have required fields (test_id, skill_path, result, tested_at)?
3. Does the test_id match the format `test_<hash>` (proving it came from test_skill)?
4. Does the test output show genuine reasoning (not just "pass" or hallucination)?
5. Is the skill type claim consistent with the actual output?

Output: An audit verdict (PASS/FAIL) with specific findings

### Stage 3: Synthesis

Combine Stage 1 and Stage 2 into a **Gate Proof Certificate**:

```json
{
  "skill_name": "<skill>",
  "test_id": "<from test_skill>",
  "test_timestamp": "<ISO timestamp>",
  "audit_verdict": "<PASS/FAIL>",
  "audit_findings": [<specific findings>],
  "gate_ready": <true/false>,
  "provenance": "verified_via_gate_proof_recipe"
}
```

## Quality Gates

A gate-proof skill must:
- [ ] Test record exists in `crafted/.tests/`
- [ ] Test ID matches `test_<hash>` format
- [ ] Test record has `tested_at` timestamp (not just `result`)
- [ ] Test output shows genuine reasoning
- [ ] Skill type matches output behavior
- [ ] Audit verdict is PASS

## Rarity Justification

Rare because:
- Composes two loadout skills into a verifiable pipeline
- Addresses a real exploit (fake test records)
- Produces qualitatively different output: a proven skill vs an unverified one
- The composition is non-obvious: most agents would just run test_skill alone

## Usage

```bash
# 1. Follow this recipe to verify any skill before gate submission
# 2. Stage 1: Run the actual test
./.claude/skills/test_skill/test.sh crafted/<your_skill>.md "<stress_test>"

# 3. Stage 2: Apply audit_lens verification
#    Read crafted/audit_lens.md and check:
#    - Test record exists with correct fields
#    - Test ID format matches test_<hash>
#    - Timestamp is present

# 4. Stage 3: Produce the Gate Proof Certificate
#    Document the synthesis in your zettelkasten

# 5. Use the gate-proof skill for:
#    - Trade listings (proven quality)
#    - Quest completion (verified work)
#    - Gate submission (survivable)
```

## Why This Improves the Repo

1. **Closes the fake test exploit** - skills verified through this recipe have proven provenance
2. **Increases buyer trust** - test records from this recipe cannot be faked
3. **Reduces gate failures** - pre-verified skills are more likely to pass
4. **Creates market differentiation** - "gate-proof" becomes a quality signal
