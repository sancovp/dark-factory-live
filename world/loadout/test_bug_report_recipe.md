---
name: test_bug_report_recipe
description: Recipe that composes test_skill + bug_report into a quality-assurance pipeline
---

# Test + Bug Report Recipe

**Type:** Recipe  
**Rarity:** Uncommon  
**Composes:** test_skill + bug_report → Quality Assurance Pipeline

## The Problem

When a skill fails a test, the failure information often gets lost. There's no automated path from "test failed" to "bug filed and tracked." This recipe closes that loop.

## The Pipeline

### Stage 1: Test the Skill

Use test_skill to run the skill under evaluation:

```bash
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
```

Capture the test_id from the output.

### Stage 2: Evaluate the Result

Check if the test passed:
- Test passed → skill is ready for trade
- Test failed → proceed to Stage 3

### Stage 3: Auto-File Bug Report

If test failed, use bug_report to file the failure:

```bash
./.claude/skills/bug_report/report.sh \
  "Skill <skill_name> fails test <test_id>" \
  "The skill produced incorrect/hallucinated output when given test input: <test_input>. Output: <output>" \
  "1. Run test_skill on <skill_path> 2. Observe incorrect output 3. This skill should not be listed" \
  medium
```

## Verdict Output

```
## QA Pipeline Verdict for <skill_name>

- Test Result: PASS/FAIL
- Bug Filed: YES/N/A
- Recommendation: LIST / DO NOT LIST
```

## Why This Improves the Repo

1. **Closed feedback loop**: test failures automatically become tracked bugs
2. **Quality gate enforcement**: failed skills don't get listed
3. **Traceability**: every listed skill has a passing test + no filed bugs

## Composition Summary

| Stage | Skill Used | Purpose |
|-------|------------|---------|
| 1 | test_skill | Execute and capture output |
| 2 | Manual evaluation | Pass/fail determination |
| 3 | bug_report | File failures for tracking |
