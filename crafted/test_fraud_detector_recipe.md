# Recipe: Test Fraud Detector
Type: Recipe
Output Type: Rare
Yield: A defensive skill that detects fabricated test records

## Ingredients
1. **lens_verify_pipeline** (Uncommon) — validates skill schema + applies second-order analysis
2. **second-order-lens** (Common) — forces examination of exploitation scenarios

## Problem Addressed
The test system stores results as JSON in `crafted/.tests/`. These files are not validated by cryptographic proof — any agent with filesystem access can fabricate passing test results without running actual tests.

## Assembly
### Step 1: Identify the Skill to Audit
Take `input_skill_path` — the skill claiming a test record.

### Step 2: Parse Test Record
```
# Look for matching test record
test_record_path = f"crafted/.tests/{skill_name}.json"
if not exists(test_record_path):
    return FAIL: "No test record found"
    
# Read test record
test_record = parse_json(test_record_path)
assert test_record.test_id matches expected pattern
assert test_record.skill_path matches input_skill_path
```

### Step 3: Apply Second-Order Lens for Exploitation Thinking
Ask:
- "What if this test record was fabricated?"
- "Who has filesystem access?"
- "What would a bad actor change to make fake tests pass?"
- "What evidence would survive scrutiny?"

### Step 4: Cross-Validation Checks
Run these checks against the test record:

1. **Schema Check**: Verify required fields exist (`test_id`, `skill_path`, `result`)
2. **Path Consistency**: Confirm `skill_path` in record matches input
3. **Result Validity**: Check `result` is one of: pass, fail, error
4. **Timestamp Plausibility**: Test timestamp should not predate skill creation
5. **Reference Integrity**: If test claims "composed_skills", verify those skills exist

### Step 5: Integration with lens_verify_pipeline
Chain the existing `lens_verify_pipeline` on the test record itself:
```
lens_verify_pipeline(crafted/.tests/{test_id}.json)
```
This applies second-order lens to the test record's own structure.

## Output Shape
```
{
  "audit_result": "PASS" | "FAIL" | "SUSPICIOUS",
  "checks_passed": [...],
  "checks_failed": [...],
  "fraud_indicators": [...],  # second-order lens findings
  "confidence": "high" | "medium" | "low"
}
```

## Expected Rarity
Rare — addresses a real exploit vector; combining schema validation + second-order exploitation thinking creates a powerful defensive tool.

## Usage
```
python -c "
from test_fraud_detector import audit_test_record
result = audit_test_record('crafted/lens_verify_pipeline.md')
print(result)
"
```

## Quality Check
- Can you fool this detector with a fake test record? (Must: no → detector needs hardening)
- Does the second-order lens find scenarios the schema check misses? (Must: yes → composition is essential)
- Would this have caught the audit_bug_exploit? (Must: yes → the recipe has value)
