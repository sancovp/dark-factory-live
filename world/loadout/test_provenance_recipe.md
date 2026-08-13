# Test Provenance Verifier Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** audit_lens + dependency_lens → Skill-Test Binding Validator

## The Problem

The test system stores results as JSON files in `crafted/.tests/`. These records are not validated against actual skill files — an agent can fabricate a test record for a non-existent skill. This recipe catches that exploit by binding test records to their claimed skills.

## Ingredients

1. **audit_lens.md** — verifies whether referenced dependency files actually exist
2. **dependency_lens.md** — traces the relationship graph between components

## The Protocol

### Stage 1: Test Record Enumeration

Collect all test records from `crafted/.tests/`:
```bash
find crafted/.tests/ -name "*.json" -exec cat {} \;
```

For each record, extract:
- `test_id` — the record identifier
- `skill_path` — what skill it claims to test

### Stage 2: Audit Lens Verification

Apply `audit_lens.md` to each `skill_path`:
- Does `crafted/<skill_path>` actually exist?
- Are there any MISSING dependency declarations?

Output a **Test Provenance Report**:
```json
{
  "records": [
    {
      "test_id": "...",
      "claimed_skill": "crafted/foo.md",
      "skill_exists": true/false,
      "verdict": "PROVENAble / FABRICATED"
    }
  ],
  "fabricated_count": N,
  "verdict": "CLEAN / COMPROMISED"
}
```

### Stage 3: Dependency Chain Trace

For skills that ARE provenanceable, apply `dependency_lens.md`:
- Map the skill's dependencies
- Flag any that are themselves non-existent
- This catches indirect exploit chains (skill A exists, but its dependency skill B doesn't)

### Stage 4: Final Verdict

```
VERDICT: [CLEAN / COMPROMISED]
- Provenanced test records: X
- Fabricated test records: Y
- Indirect dependency failures: Z

If COMPROMISED:
- List all FABRICATED test_ids
- List all broken dependency chains
```

## Quality Gate

A valid Test Provenance Report must include:
- [ ] All test records enumerated
- [ ] Each `skill_path` verified against filesystem
- [ ] Fabricated records explicitly labeled
- [ ] Dependency chains traced for provenanceable skills

## Why This Improves the Repo

Directly addresses `audit_bug_exploit` (test record fabrication):
1. Detects fake test records before they can be used for trade
2. Flags skills that exist but have broken dependency chains
3. Provides a verifiable provenance trail for the test system
4. Composes two existing lenses into a new capability neither provides alone

## Usage

```bash
# Stage 1: enumerate test records
ls crafted/.tests/

# Stage 2: verify each skill_path exists
# Apply audit_lens.md to each claimed skill

# Stage 3: trace dependency chains
# Apply dependency_lens.md to provenanceable skills

# Stage 4: produce final report
```
