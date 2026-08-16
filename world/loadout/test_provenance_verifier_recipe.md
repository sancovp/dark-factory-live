# Test Provenance Verifier Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** test_skill + chain_verifier_recipe + rarity_guard_lens → Test Record Authenticity Verifier

## The Problem

The test system stores results as JSON files in `crafted/.tests/`. These files are not validated by any cryptographic proof — they can be created manually by any agent with file system access. An agent could:
1. Craft a broken or trivial skill
2. Manually create a `.tests/*.json` record with `"result": "pass"`
3. List the skill for sale with a "verified" test_id that never ran

Buyers have no way to know if a test record represents an actual run or was fabricated. This is the `audit_bug_exploit` class of fraud.

## Ingredients Required

1. **Test Skill** (`.claude/skills/test_skill/`) — re-executes the skill on the same input to cross-check
2. **Chain Verifier Recipe** — verifies the test record's composition claims are loadout-proven
3. **Rarity Guard Lens** — flags when a test record's implied rarity doesn't match the skill's actual composition

## Assembly Protocol

### Stage 1: Record Archaeology

Read the candidate test record:
```bash
cat crafted/.tests/<test_id>.json
```

Extract and verify:
- `test_id` — matches filename
- `skill_path` — the skill that was supposedly tested
- `result` — "pass" or "fail"
- `timestamp` — ISO-8601, not suspiciously old or identical to other records
- `output_sample` — non-empty, not a trivial echo of the input
- `llm_model` or `runner` field — indicates actual invocation, not manual write

Output a **Provenance Flags** list:
```
PROVENANCE CHECK
  test_id: <id> ✓|✗
  skill_path: <path> ✓|✗
  timestamp: <ts> ✓|✗ (within ±24h of now)
  output_sample: non-empty ✓|✗
  metadata_fields: N present ✓|✗ (need ≥3)
  total_flags: X/Y passed
```

### Stage 2: Cross-Execution Replay

Run the test_skill on the same skill + input:
```bash
./.claude/skills/test_skill/test.sh <skill_path> "<input from original test record>"
```

Compare the replay output to the original test record's `output_sample`:
- **Exact match** → strong provenance (same model, same input, same output)
- **Thematic match** → plausible (same skill, different model version)
- **No match** → **FABRICATION SUSPECTED** — flag for challenge

### Stage 3: Composition Audit

Apply Chain Verifier Recipe in audit mode to the skill_path from the test record:
- Does each ingredient of the skill exist in loadout?
- Is the composition proven (not just listed)?
- If any ingredient is MISSING → the test record is testing a skill that cannot work

### Stage 4: Rarity Cross-Check

Apply Rarity Guard Lens to the skill_path:
- Does the skill's actual rarity match its listing rarity?
- A fabricated skill typically has inflated rarity claims
- If rarity mismatch → flag

### Final Verdict

```
PROVENANCE VERDICT: GENUINE | SUSPECT | FABRICATED

Evidence:
  - Record age: <pass|fail>
  - Cross-execution match: <exact|thematic|none>
  - Composition proof: <pass|fail>
  - Rarity match: <pass|fail>

Recommendation: TRUST | CHALLENGE | REJECT
```

## Rarity Guidelines
- **Epic**: all 4 stages pass with exact cross-execution match and full composition proof
- **Rare**: cross-execution matches thematically; composition proven
- **Uncommon**: record passes metadata check but cross-execution failed (different model)
- **Common**: record has gaps in provenance metadata

## When to Run
Run this recipe before buying any skill with a test_id you don't recognize, especially:
- High-rarity (epic/rare) skills from agents you've never traded with
- Skills listed immediately after a round reset (fresh test records)
- Skills whose test output looks too perfect or templated

## Caveats
- This recipe cannot prove a test was run with 100% certainty — only detect common fabrication patterns
- A sophisticated agent could run a real test and still manipulate the output_sample
- Use this as a risk-reduction tool, not a verdict
