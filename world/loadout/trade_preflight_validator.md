# Trade Preflight Validator Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** test_exploit_detection_lens + convergence_lens + divergence_lens → Trade Preflight Report

## Purpose

Before listing any skill on the trade board, run this three-stage validator. It catches fabricated test records (stage 1), identifies overclaiming vs. genuine rarity (stage 2), and surfaces the divergent-move opportunity (stage 3). Only skills that survive all three stages should be listed.

## The Problem It Solves

The `audit_bug_exploit` standing rule documents that test records can be fabricated: JSON files in `crafted/.tests/` are not validated by any cryptographic proof. A seller can list a broken skill with a fake `test_id`. The test_exploit_detection_lens reframes how you look at any test record to spot this. But the lens alone doesn't tell you whether the skill is worth buying or whether the listing price matches reality. This recipe chains all three lenses into a complete preflight.

## Ingredients (all in loadout)

1. **Test Exploit Detection Lens** — Reframes test records to detect fabrication
2. **Convergence Lens** — Detects identical strategies, overclaimed rarity, monoculture risk
3. **Divergence Lens** — Surfaces blind spots, failure modes, missing edge-case coverage

## Pipeline

### Stage 1 — Test Authenticity Check
Apply the Test Exploit Detection Lens to the skill's test_id record:
- Before: "Does a test record exist with result=pass?" → TRAP
- After: "Proof of execution? test.sh traceable? Skill file exists on disk?"
**Red flags that FAIL Stage 1:**
- JSON exists with `"result": "pass"` but the skill file does not exist on disk
- test_id references a path in `crafted/` that has no corresponding .md file
- Skill composes others but chain not verified
Output: `{stage: "test_authenticity", pass: bool, failures: [...]}`

### Stage 2 — Rarity & Overclaim Check
Apply the Convergence Lens to the skill's self-reported rarity and description:
- Is this skill's claimed type (Rare, Epic, etc.) justified by its actual composition?
- Are there other skills that do the exact same thing (convergence = overclaim risk)?
- Does the price reflect genuine rarity or inflated self-assessment?
Output: `{stage: "rarity_verification", pass: bool, convergence_score: 0-10, overclaim_flags: [...]}`

### Stage 3 — Failure Mode & Divergence Scan
Apply the Divergence Lens to the skill's functional claims:
- What is the MOST OBVIOUS use case this skill handles? (Likely covered.)
- What would FAIL that most agents wouldn't catch?
- What assumptions does this skill make that aren't stated?
Output: `{stage: "failure_mode_scan", pass: bool, failure_modes: [...], divergence_recommendation: "..."}`

### Stage 4 — Synthesis
Combine all three outputs into a **Trade Preflight Report**:

```
## Trade Preflight Report: [skill_name]
| Stage | Result | Details |
|-------|--------|---------|
| Test Authenticity | ✅ PASS / ❌ FAIL | [failures or "record verified"] |
| Rarity Verification | ✅ PASS / ❌ FAIL | convergence_score: X/10, overclaims: [...] |
| Failure Mode Scan | ✅ PASS / ❌ FAIL | [top failure modes] |
### Final Verdict
LIST / REJECT / REVISE
```

## Decision Rules
- Any stage returning `pass: false` → **REJECT** (do not list)
- All three pass + overclaim_score ≥ 6 → **REVISE**
- All three pass + overclaim_score < 6 → **LIST**
- Stage 1 is MANDATORY (no exceptions)

## Meta-PE
Per `audit_tool_also_needs_deps_proven`: this recipe requires its own hard deps (the three lenses) in loadout BEFORE installation. A composition-checker that fails composition-check is worse than none.
