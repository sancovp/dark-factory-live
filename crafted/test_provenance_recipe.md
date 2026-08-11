# Recipe: Test Provenance Verifier
Type: Recipe
Output Type: Defensive (Rare)
Yield: 1 skill that detects fabricated test records by verifying execution trace

## Ingredients
1. **File Existence Prosthesis** — checks that skill_path in test record actually exists
2. **Second-Order Lens** — asks "what would a fabricator claim vs what actually happened?"
3. **Schema Validator Template** — confirms test record has required fields

## Assembly
1. **Input**: A test record JSON (from `.tests/`)
   ```json
   {
     "test_id": "...",
     "skill_path": "...",
     "result": "pass|fail",
     "timestamp": "ISO8601"
   }
   ```

2. **Stage 1 — Skill Existence Check (prosthesis)**:
   - Verify `skill_path` points to a real file in the repo
   - Verify `skill_path` is a valid skill (has required frontmatter: name, type)
   - FAIL: file missing → test is fabricated
   - FAIL: file exists but invalid schema → test is unverifiable

3. **Stage 2 — Timestamp Plausibility Check (second-order lens)**:
   - Ask: "What would a lazy fabricator set as timestamp?"
     - Answer: Current time, or no timestamp
   - Check: Is timestamp plausible? (not future, not pre-repo-creation)
   - Check: Does timestamp correlate with skill's last-modified time?
   - FAIL: timestamp predates skill creation → fabricator didn't actually test

4. **Stage 3 — Execution Trace Validation**:
   - Look for side-effects of actual test execution:
     - `.tests/` directory must exist
     - test record must be one of many (suggests systematic testing)
     - skill's `.tests/` must contain the claimed test_id
   - Question: "Would a fabricator create a whole test directory structure?"
   - Answer: No → presence of structured test dir suggests real execution

5. **Stage 4 — Composition Verification**:
   - If test skill is itself a recipe, verify claimed components exist
   - This catches fabricated compositions

## Output
```
Test Provenance Report:
- skill_path: <path>
- test_id: <id>
- EXISTS: ✓/✗
- VALID_SCHEMA: ✓/✗  
- PLAUSIBLE_TIMESTAMP: ✓/✗
- HAS_EXECUTION_TRACE: ✓/✗
- COMPOSITION_VALID: ✓/✗
- VERDICT: PASS / FAIL (FABRICATED) / FAIL (UNVERIFIABLE)
```

## Quality Check
- Fabricated record (timestamp now, no test dir) → MUST detect
- Real record (skill tested, directory exists) → MUST pass
- Unverifiable record (skill exists but no test dir) → MUST flag

## Expected Rarity
Uncommon — addresses a specific exploit (audit_bug_exploit: test records can be fabricated)

## Why This Recipe Works
Fabricated test records fail at least one stage:
- Stage 1: referenced skill doesn't exist
- Stage 2: timestamp is implausible or missing
- Stage 3: no execution trace (no test directory structure)
- Stage 4: claimed composition references missing skills

Each stage catches a different fabricator error pattern. All four stages together make fabrication nearly impossible without actually running the test.
