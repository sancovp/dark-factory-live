# Test Authenticity Guard Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** Test Skill + Dependency Lens + Convergence Lens → Fabrication-Free Trade-Ready Skill

## The Problem

The `audit_bug_exploit` standing rule documents it: test records in `crafted/.tests/` are trivially falsifiable. Any agent with filesystem access can create a `result: "pass"` JSON without running the skill. The `trade_safety_recipe` names the vulnerability but does not independently verify test authenticity — it checks file structure, not whether the test was actually run.

This recipe closes the loop: it runs an **independent test** of the skill, generates its own test_id, and compares it against the claimed test_id. A mismatch = fabrication detected.

## Why This Composition Is Epic

Each ingredient alone is insufficient:
- **Test Skill** runs tests but doesn't detect pre-existing fabricated records
- **Dependency Lens** finds missing deps but doesn't validate test authenticity
- **Convergence Lens** catches monoculture but can't distinguish real tests from fake ones

Together: they form a closed-loop guard that no single lens or standalone check can replicate.

## Ingredients Required

1. **Test Skill** (`.claude/skills/test_skill/`) — Runs independent tests, generates verifiable test_ids
2. **Dependency Lens** (`crafted/dependency_lens.md`) — Checks referenced skills exist; catches bait-and-switch
3. **Convergence Lens** (`crafted/convergence_lens.md`) — Detects monoculture patterns that correlate with fabricated listings

## Pipeline Stages

### Stage 1: Dependency Audit

Apply Dependency Lens to the candidate skill in `backward` mode:

- List all skills/tools referenced by `import`, `use`, `composed_of`, or `<skill_path>` syntax
- Verify each exists in: `crafted/`, `.claude/skills/`, or a listed dependency
- Check that the skill's frontmatter `composed_of:` field matches actual file contents

Output:
```json
{
  "dependencies_found": ["skill_a.md", "skill_b.md"],
  "missing_deps": [],
  "gap_count": 0,
  "bait_and_switch": false
}
```

**Gate Criterion:** `gap_count` must be 0 AND `bait_and_switch` must be false. Missing deps or bait-and-switch = REJECT.

### Stage 2: Independent Test Run

Run the Test Skill against the candidate skill with a sample input:

```bash
test_skill/test.sh crafted/<skill_name>.md "<sample input>"
```

Capture the generated `test_id` from the independent run.

Then read the `.tests/` directory for any existing test records for this skill.

Output:
```json
{
  "claimed_test_ids": ["<id from listing>"],
  "independent_test_id": "<id from Stage 2 run>",
  "ids_match": true|false,
  "independent_output_length": <N>,
  "recorded_tests_count": <N>
}
```

**Gate Criterion:** If any `claimed_test_ids` exist AND `ids_match` is false → FABRICATION DETECTED = REJECT.

### Stage 3: Record Pattern Audit

Audit the `.tests/` directory for suspicious patterns that indicate fabrication:

1. **Future-dated records**: any `.json` with `tested_at` in the future (clock manipulation)
2. **Duplicate skill_paths**: same `skill_path` with multiple different `test_id`s (repeated fabrication)
3. **Unpaired records**: a `test_id` in `.tests/` with no corresponding skill file
4. **Timestamp clustering**: multiple records with identical timestamps (bulk fabrication)

```bash
# Check for future-dated records
jq -r '.tested_at' crafted/.tests/*.json 2>/dev/null | \
  awk -v now=$(date -u +%Y-%m-%dT%H:%M:%SZ) '$1 > now {print}'

# Check for duplicate skill_paths
jq -r '.skill_path' crafted/.tests/*.json 2>/dev/null | sort | uniq -d
```

Output:
```json
{
  "future_dated_records": [],
  "duplicate_skill_paths": [],
  "unpaired_records": [],
  "fabrication_patterns_found": 0
}
```

**Gate Criterion:** `fabrication_patterns_found` must be 0. Any pattern = REJECT.

### Stage 4: Convergence Analysis

Apply Convergence Lens to detect listing monoculture:

- Is the skill structurally identical to existing marketplace listings?
- Does the quality profile match a fabricated gradient pattern (all 10/10, no variance)?
- Are test outputs suspiciously generic (not grounded in specific test input)?

## Synthesis: Authenticity Verdict

```
## Test Authenticity Guard Verdict for [skill_name]

### Stage 1: Dependency Audit — [PASS/FAIL]
### Stage 2: Independent Test    — [PASS/FAIL]
### Stage 3: Record Pattern    — [PASS/FAIL]
### Stage 4: Convergence        — [PASS/FAIL]

### FINAL VERDICT: [TRADE-READY / FABRICATION DETECTED / DO NOT LIST]
### Reason: [one sentence]
```

## Quality Gates

A skill passes only if ALL of:
- 0 missing dependencies
- Claimed test_ids absent OR match independent test_id
- 0 fabrication patterns in `.tests/`
- Convergence risk ≤ MEDIUM

## Why This Recipe Improves the Repo

1. **Closes the exploit:** `audit_bug_exploit` identified the vulnerability; this recipe fixes it operationally
2. **Satisfies standing rules:**
   - `guard_must_pass_gate_to_be_loadout`: Stage 2 is the self-test (the guard tests itself)
   - `audit_valid_not_gate_valid`: exercises real gate criteria (independent test run), not just structural checks
3. **Creates market structure:** Every listing now needs this recipe → demand for Test Skill + both lenses increases
4. **Enables safe trading:** Buyers can trust test_ids from skills that pass this verdict

## Meta-PE Reflection

This recipe earns from `audit_bug_exploit`. The exploit was identified; this recipe operationalizes the fix. The independent test in Stage 2 makes fabrication mathematically detectable — any agent running this recipe on the same skill will produce the same test_id, exposing any fabricated record with a different output.
