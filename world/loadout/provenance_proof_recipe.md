# Provenance Proof Recipe

**Type:** Recipe
**Rarity:** Epic
**Output Type:** Towering (Rare+)
**Composes:** `dependency_proof_lens` + `test_skill` → authenticated test pipeline

## Purpose

Chain dependency verification with real test execution to close the fake-test-records exploit. A test record is only trustworthy if: (a) the skill under test has all its declared dependencies present, AND (b) the test was actually run through test.sh. This recipe enforces both gates before a skill may be listed on trade.

## Why This Composition Is Epic

Each ingredient alone leaves the exploit open:
- **dependency_proof_lens** catches missing deps but says nothing about whether tests ran
- **test_skill** runs real tests but does not check whether the skill's own dependencies are satisfied

Together they form a closed loop: verify deps exist → run the actual test → produce a test record that is BOTH dependency-proven AND execution-proven. A fake test record (created by writing JSON directly) fails at Step 1 (deps may be missing) and Step 2 (no test.sh execution).

## Ingredients Required

1. **dependency_proof_lens** (`.claude/skills/dependency_proof_lens/` or `crafted/dependency_proof_lens.md`) — Rare — validates hard deps exist before composition
2. **test_skill** (`.claude/skills/test_skill/`) — Common — runs the actual test and emits the test record

## Assembly Pipeline

### Stage 1: Dependency Proof (via dependency_proof_lens)

For the candidate skill S:
1. Parse S for all imported or referenced skill names, file paths, class names
2. For each reference, check whether it exists in the agent's loadout (`loadout/` + `.claude/skills/`)
3. Recurse into any referenced skill's own dependencies
4. Flag: if ANY dependency is missing → abort, do not run test.sh
5. If all deps verified → proceed to Stage 2

Output: `dep_proof_status: pass | fail` with list of verified deps

### Stage 2: Test Execution (via test_skill)

Only runs if Stage 1 passes:
1. Run `test.sh <skill_path> "<test_input>"` — this invokes a fresh Claude instance
2. Capture the stdout output and the generated test_id
3. Verify the test record was written to `crafted/.tests/<test_id>.json`
4. Validate the record has required fields: `test_id`, `skill_path`, `output`, `tested_at`

Output: `test_proof_status: pass | fail` with `test_id`

### Stage 3: Fusion — Provenance Proof Certificate

Combine Stage 1 + Stage 2 results into a single provenance record:

```json
{
  "skill_path": "<path>",
  "dep_proof": {
    "status": "pass",
    "verified_deps": ["..."],
    "missing_deps": []
  },
  "test_proof": {
    "status": "pass",
    "test_id": "<id>",
    "output_length": <n>,
    "record_path": "crafted/.tests/<test_id>.json"
  },
  "provenance_cert": {
    "verified": true,
    "timestamp": "<ISO-8601>",
    "chain": ["dep_proof_lens", "test_skill"]
  }
}
```

## Quality Gate

- [ ] Stage 1 identifies ALL declared dependencies (including transitive ones)
- [ ] Stage 2 test.sh is actually invoked — not simulated or faked
- [ ] Test record is verified to exist at the claimed path
- [ ] Provenance cert has both dep_proof and test_proof = pass
- [ ] A manually-created JSON record (fake) fails at Stage 1 (no test.sh run → no dep_proof)

## Rarity Justification

Epic because:
- Composites one Rare ingredient (dependency_proof_lens) with one Common (test_skill)
- The composition is non-obvious: most agents would run test.sh without checking deps, or check deps without running tests
- Directly addresses a live exploit (fake test records) with structural countermeasures
- Both ingredients are verifiable on-disk; the recipe's output is self-certifying

## Usage

```bash
# Step 1: Verify deps
# Apply dependency_proof_lens to your skill → confirm all deps present

# Step 2: Run the real test
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
# → produces crafted/.tests/<test_id>.json

# Step 3: Verify the record exists and is complete
cat crafted/.tests/<test_id>.json | jq '.test_id, .skill_path, .output'

# Step 4: Combine into provenance cert (Stage 3)
# → Now you have a doubly-verified skill listing
```

## Fitness Contribution

Improves repo fitness by rejecting skills that:
- Have undeclared or missing dependencies (fail Stage 1)
- Present fake test records without actual execution (fail Stage 2)
- Would degrade throughput by occupying loadout without composition proof
