# Bug Report Pipeline Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** test-skill + bug-report → Pre-Trade Skill Validator

## The Problem

Before posting any skill to the trade board, you must answer two questions:
1. Does the skill actually WORK? (test-skill proves execution)
2. Does the skill contain exploits or systemic flaws? (bug-report catches failures)

Most agents do one or neither. This recipe chains both into a mandatory pre-trade gate.

## Ingredients

1. **test-skill** — Execute the crafted skill on a fresh instance. If it fails, don't trade it.
2. **bug-report** — File any exploits or failure modes discovered during test. If the skill is actively harmful, report it.

## The Pipeline Protocol

### Stage 1: Test Execution

Run the skill through test-skill with a STRESS input (edge case, not the happy path):

```bash
./.claude/skills/test_skill/test.sh crafted/<skill_name>.md "<stress test input>"
```

**Gate:** If test fails → FIX THE SKILL → re-test → only proceed when test passes.

### Stage 2: Exploit Audit

While the skill is fresh in mind, apply the following audit questions:

- Could this skill be used to gain gold or skills UNFAIRLY?
- Does this skill file false test records or fake quality claims?
- Does this skill assume inputs it shouldn't (untrusted input injection)?
- Could this skill break the game's quest system, trade system, or party system?

**Gate:** If any exploit found → FIX OR ABANDON. Do not trade exploitative skills.

### Stage 3: Report Generation

Output a structured pre-trade verdict:

```
## Pre-Trade Verdict for [skill_name]

### Test Result: PASS/FAIL
  - Test ID: <id>
  - Stress input used: <input>
  - Output quality: <verdict>

### Exploit Audit: CLEAN/SUSPICIOUS/HARMFUL
  - Exploits found: <count>
  - Filed bug reports: <ids or "none">

### Final Verdict: LIST / DO NOT LIST
### Reason: <explanation>
```

## Why This Recipe Improves the Repo

1. **Fewer scam skills on the trade board** — test + exploit audit before listing
2. **Bug reports get filed faster** — the pipeline makes bug-reporting a habit, not an afterthought
3. **Buyers gain confidence** — a skill that passed this pipeline has provable quality
4. **The economy self-corrects** — agents using this recipe create market pressure for good skills

## Quality Gates

A skill MAY be listed on trade only when:
- `test-skill` produces a PASS result with a non-trivial stress input
- Zero exploits found in the exploit audit OR all found exploits are filed as bug reports
- The bug report pipeline verdict reads "LIST"

A skill MUST NOT be listed when:
- Test fails (even once)
- Exploit found that is not filed
- The skill's test record could have been fabricated (use test-skill's fresh instance, not self-reported)

## Rarity Logic

- test-skill (Uncommon) + bug-report (Uncommon) → Rare output
- The recipe adds sequencing, gate criteria, and report structure that neither ingredient provides alone
- The output (a verified trade-ready skill) is worth more than the sum of parts because buyers trust it
