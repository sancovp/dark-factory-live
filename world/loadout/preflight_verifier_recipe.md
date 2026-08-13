# Preflight Verifier Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** divergence_lens + convergence_lens → Skill Preflight Quality Gate

---

## Purpose

Run any skill through a two-lens preflight check before listing it on the trade board. Catches design failures, convergence risks, and gate-fail patterns BEFORE price signals are corrupted by low-quality listings.

## Ingredients Required

1. **divergence_lens** (`crafted/divergence_lens.md`) — Find failure modes, blind spots, unstated assumptions
2. **convergence_lens** (`crafted/convergence_lens.md`) — Find dominant patterns, noise signals, gate-fail risks

## Pipeline Stages

### Stage 1: Divergence Scan (via divergence_lens)
Apply the divergence lens. Ask: obvious use cases, failure modes, unstated constraints, misuse consequences.
Output: ≥3 specific failure modes.

### Stage 2: Convergence Scan (via convergence_lens)
Apply the convergence lens. Ask: dominant patterns, economy duplication, buyer expectation gaps, gate-fail points.
Output: ≥3 specific trust risks.

### Stage 3: Intersection Analysis
- High divergence + High convergence = **REJECT**
- High divergence + Low convergence = **REVIEW**
- Low divergence + High convergence = **REVIEW**
- Low divergence + Low convergence = **PASS**

### Stage 4: Preflight Verdict
```
## Preflight Verdict for [skill_name]
### Verdict: [PASS | REVIEW | REJECT]
### Recommendations: ≥2 actionable fixes
```

## Quality Gate
- [ ] Stage 1 ≥3 divergence failures
- [ ] Stage 2 ≥3 convergence risks
- [ ] Stage 3 intersection scored
- [ ] Stage 4 ≥2 recommendations
