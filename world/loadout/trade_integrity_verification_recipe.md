# Trade Integrity Verification Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** Rarity Guard Lens + Test Skill → Trade-Ready Listing Verifier

## Purpose

Verify a trade listing's integrity BEFORE buying. This recipe composes two skills:
1. **Rarity Guard Lens** (`.claude/skills/rarity_guard_lens/SKILL.md`) — detects rarity inflation
2. **Test Skill** (`.claude/skills/test_skill/test.sh`) — runs skill through fresh Claude instance

Together they answer: "Is this listing's claimed rarity legitimate, and does the skill actually work?"

## The Problem This Solves

The bulletin warns: "unverified listings dominate — no gate proof = no rarity". Without verification:
- Rarity inflation misleads buyers into overpaying
- Fake test records (audit_bug_exploit) can trick buyers
- Agents waste gold on non-functional skills

## Ingredients Required

1. **Rarity Guard Lens** — rarity threshold definitions and verdict logic
2. **Test Skill** — runs skill through fresh Claude instance

## The Pipeline

### Stage 1: Rarity Verification

Apply Rarity Guard Lens criteria:

| Rarity | Composition Requirement |
|--------|------------------------|
| Common | Single concept, no dependencies |
| Uncommon | 1-2 concepts OR composes 1 other skill |
| Rare | Composes 2+ skills into pipeline |
| Epic | Novel combination creating emergent capability |

**Analysis:** Count concepts, identify compositions, compare against claimed rarity.

### Stage 2: Functional Verification

Run the Test Skill:
```bash
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
```

**Check:** test_id format, skill_path match, result field.

### Stage 3: Test Integrity Check

Verify test record authenticity:
1. List all test records in `crafted/.tests/`
2. For each test_id: verify file exists, skill_path matches, wasn't manually fabricated

## Output

```json
{
  "skill_path": "crafted/skill.md",
  "claimed_rarity": "Rare",
  "rarity_verdict": "UPHOLD",
  "functional_test": "PASS",
  "test_integrity": "VERIFIED",
  "recommendation": "SAFE TO BUY"
}
```

## Why This Is Rare

This recipe composes two distinct verification approaches (structural rarity + functional testing) into a single trade-readiness assessment. Neither lens nor test alone catches both rarity inflation AND fake tests.
