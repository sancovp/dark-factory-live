# Recipe: Systemic Risk Detector

**Type:** Recipe
**Rarity:** Epic
**Composes:** dependency_lens + divergence_lens + monoculture_detector → Systemic Skill Economy Risk Assessment

## Purpose

Detect systemic risks in the skill economy before they cascade into failures. This recipe combines three analytical lenses to identify:
1. **Dependency hotspots** — single points of failure
2. **Failure mode cascades** — how one failure propagates
3. **Monoculture traps** — when everyone does the same thing and the system becomes fragile

## Why This Composition Is Epic

Each lens alone catches one dimension of risk:
- **Dependency Lens** finds structural vulnerabilities but doesn't predict failure propagation
- **Divergence Lens** surfaces failure modes but treats them as isolated
- **Monoculture Detector** finds convergent behavior but doesn't trace why agents converge

Together they form a complete risk assessment: structure → failures → causes → systemic verdict.

## Ingredients Required

1. **Dependency Lens** (`crafted/dependency_lens.md`) — Maps structural dependencies between skills
2. **Divergence Lens** (`crafted/divergence_lens.md`) — Identifies failure modes in skill compositions
3. **Monoculture Detector Pipeline** (`crafted/monoculture_detector_pipeline.md`) — Detects convergent behavior patterns

## Pipeline Steps

### Stage 1: Dependency Mapping (via dependency_lens)

For the skill ecosystem under analysis:
1. Identify all skill types present (Template, Lens, Recipe, etc.)
2. Map dependencies between skills (which skills reference which)
3. Identify hub skills (referenced by many others — single points of failure)
4. Trace dependency chains to root dependencies
5. Flag circular dependencies or tight coupling clusters

Output: **Dependency Graph** with hub skills highlighted and risk scores per cluster.

### Stage 2: Cascade Analysis (via divergence_lens)

For each hub skill identified in Stage 1:
1. What is the hub skill's failure mode?
2. What skills depend on the hub? (cascade surface)
3. What would happen if the hub skill failed or was reverted?
4. How quickly would the cascade propagate?
5. Are there fallback paths for dependent skills?

Output: **Cascade Report** listing failure propagation chains with impact estimates.

### Stage 3: Convergence Root Cause (via monoculture_detector)

For each high-impact cascade identified in Stage 2:
1. What market conditions caused agents to converge on this hub skill?
2. Are there alternative designs that would reduce convergence pressure?
3. What policy or recipe changes would break the monoculture safely?

Output: **Convergence Analysis** with actionable recommendations to reduce systemic fragility.

### Stage 4: Synthesis — Systemic Risk Verdict

Combine all three stages into a final risk assessment:

```json
{
  "ecosystem_snapshot": "<timestamp and scope of analysis>",
  "hub_skills": [{"skill": "...", "dependents": N, "risk_score": "high/med/low"}],
  "cascade_chains": [{"hub": "...", "cascade_to": [...], "impact": "...", "recovery_time": "..."}],
  "monoculture_pressure": "<description of convergence forces>",
  "systemic_risk_level": "critical/high/medium/low",
  "recommendations": [
    {"action": "...", "target": "...", "expected_impact": "..."}
  ]
}
```

## Quality Gate

- [ ] Stage 1 identifies at least 3 hub skills (or documents why fewer exist)
- [ ] Stage 2 traces at least 2 cascade chains with impact estimates
- [ ] Stage 3 explains WHY convergence happened (not just that it did)
- [ ] Stage 4 produces a risk level that matches the chain of evidence
- [ ] Recommendations are specific and actionable (not generic)

## Rarity Justification

Epic because:
1. Composites three uncommon ingredients (dependency_lens + divergence_lens + monoculture_detector)
2. Produces qualitatively different output than any single lens — the whole exceeds the sum
3. Addresses a real systemic risk (the economy can fail from cascade, not just individual failures)
4. The composition is non-obvious — most agents would apply one lens, not chain three
5. Directly improves the codebase by surfacing risks before they become failures
