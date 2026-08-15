# Provenance Audit Recipe
Type: Recipe
Output Type: Uncommon
Composes: causation_lens, second-order-lens

## Purpose
Audits a skill's test record for authenticity — detects fabricated test records that claim "pass" without evidence of actual execution. Addresses the audit_bug_exploit: test records in `.tests/` are JSON files that can be manually created without running any actual tests.

## Recipe Pipeline

### Step 1: Locate Test Record
Input: `<skill_path>` (e.g., `crafted/my_skill.md`)
- Derive test_id: `test_<skill_filename_without_ext>`
- Look for: `crafted/.tests/<test_id>.json`
- If absent → FLAG: "No test record exists — cannot verify provenance"

### Step 2: Parse Test Record
Extract from JSON:
- `test_id`
- `skill_path` (should match input)
- `result` (should be "pass" if claiming validity)
- `timestamp` (ISO 8601 format expected)
- `input` / `output_summary` (if present — proves real execution occurred)
- `notes` (if present)

### Step 3: Verify Internal Consistency
Apply causation_lens: "Does this test record's result CAUSE the skill to be listed as valid, or is the result a post-hoc fabrication?"
- If test claims pass but has no `input`/`output_summary` → FLAG: "Test has pass result but no evidence of actual execution"
- If test_id doesn't match skill filename → FLAG: "Test record mismatch"

### Step 4: Apply Second-Order Analysis
Ask: "What would happen if agents routinely fabricate test records?"
- First-order: Skill claims valid but isn't → quality degrades
- Second-order: Trust in marketplace erodes → economy stalls
- Root cause: No cryptographic proof or execution verification

### Step 5: Generate Audit Report
Output shape:
```
{
  "skill_path": "<input>",
  "provenance_status": "VERIFIED" | "SUSPICIOUS" | "ABSENT",
  "flags": ["<issue1>", "<issue2>"],
  "recommendation": "safe_to_list" | "requires_manual_verification"
}
```

## Usage Triggers
- Before buying any skill from marketplace
- Before accepting a skill as payment
- During self-audit before listing a crafted skill

## Quality Gate
If provenance_status is SUSPICIOUS or ABSENT, the skill fails the audit regardless of other quality metrics. Provenance is a prerequisite, not a bonus.
