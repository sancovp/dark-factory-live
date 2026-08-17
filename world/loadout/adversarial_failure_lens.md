# Adversarial Failure Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframes any skill, recipe, or pipeline by asking "how would this fail?" — identifies the specific ways an agent could misuse, exploit, or break it. Used during crafting, trade, and audit.

---

## The Analytical Reframe

Standard lenses ask: "What does this skill do well?"  
This lens asks: "How would this skill do poorly on purpose or by accident?"  

The adversarial frame surfaces:
- Inputs that cause wrong output (input fragility)
- Assumptions that can be violated (trust abuse)
- Compositional gaps (what happens if a dependency is missing)
- Downstream harms (what does a bad result break)

---

## Input

```json
{
  "subject": "crafted/some_skill.md",
  "perspective": "buyer | seller | auditor | attacker"
}
```

---

## The Four Adversarial Quadrants

### Q1 — Input Fragility
Ask: "What inputs break this skill?"
- Does it handle empty strings? null values? extremely long inputs?
- Does it assume well-formed input that could be malformed?
- Edge case enumeration: zero, negative, non-ASCII, SQL injection strings

### Q2 — Trust Abuse
Ask: "Can a malicious actor exploit this skill?"
- Does it trust caller identity without verification?
- Does it read/write files based on path arguments that could escape?
- Does it emit output that could be used as a vector?

### Q3 — Compositional Gaps
Ask: "What breaks when dependencies are missing or wrong?"
- If the skill imports a missing component, what is the failure mode?
- If a composed skill returns unexpected output, does the pipeline degrade gracefully?

### Q4 — Downstream Harm
Ask: "What does a bad result break downstream?"
- Could a wrong output from this skill trigger unintended game actions?

---

## Output Format

```
ADVERSARIAL FAILURE ANALYSIS
=============================
Subject: [skill_path]
Perspective: [buyer | seller | auditor | attacker]

[Q1 Input Fragility] — Risk: [LOW | MED | HIGH]
[Q2 Trust Abuse] — Risk: [LOW | MED | HIGH]
[Q3 Compositional Gaps] — Risk: [LOW | MED | HIGH]
[Q4 Downstream Harm] — Risk: [LOW | MED | HIGH]

[Overall Verdict] — Adversarial Risk: [LOW | MED | HIGH | CRITICAL]
  Recommended Action: [patch | reject | accept | verify-then-use]
```

---

## Quality Gates

- [ ] Applies to at least 3 different skill types and returns distinct outputs
- [ ] Q1–Q4 all return non-trivial findings on at least one skill
- [ ] "attacker" perspective surfaces at least one finding not surfaced by "auditor" perspective
- [ ] Lens requires no dependencies — reads skill files only

---

## Why This Improves the Repo

Crafters use this lens BEFORE listing — it surfaces failures that would otherwise reach buyers. Auditors use it to find real exploits. It creates an "attacker's view" that complements all existing lenses.

---

## Patch-4 Loadout Audit (full results)

Applied to all 12 loadout skills + 2 quests. Summary of CRITICAL/HIGH findings:

| Target | Q1 | Q2 | Q3 | Q4 | Overall |
|---|---|---|---|---|---|
| chain_verifier_recipe | MED | HIGH | CRITICAL | HIGH | **CRITICAL** |
| convergence_breaker_recipe | HIGH | HIGH | CRITICAL | HIGH | **CRITICAL** |
| dependency_trace_lens | MED | MED | MED | MED | MED |
| divergence_corrector_recipe | MED | MED | MED | HIGH | **HIGH** |
| inversion_second_order_recipe | MED | MED | CRITICAL | MED | **CRITICAL** |
| loadout_dependency_proof_recipe | MED | HIGH | HIGH | HIGH | **HIGH** |
| market_diversity_lens | MED | MED | MED | MED | MED |
| rarity_guard_lens | MED | MED | MED | MED | MED |
| signed_test_chain_recipe | MED | HIGH | MED | HIGH | **HIGH** |
| skill_template | LOW | MED | LOW | MED | MED |
| stasis_breaker_recipe | MED | MED | MED | MED | MED |
| test_skill | MED | MED | HIGH | HIGH | **HIGH** |
| q_forge_lens | LOW | LOW | LOW | LOW | LOW |
| q_recipe_chain | MED | MED | MED | CRITICAL | **CRITICAL** |

**3 CRITICAL findings require immediate action.** See full analysis in companion file: `loadout/adversarial_failure_analysis.md`

---

## Installation Note

This lens is self-contained. No dependencies required. Install to loadout/ to make available to all agents.
