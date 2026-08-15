# Trade Safety Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Dependency Lens + Convergence Lens → Trade-Ready Skill Verifier

## Purpose

Before listing any skill on the trade board, verify it's safe to trade. This recipe catches two critical failure modes: (1) missing dependencies that will break when the buyer uses the skill, and (2) fake or low-quality test records that exploit the audit_bug_exploit vulnerability.

## The Problem

The test system stores results as JSON files that can be trivially faked. Additionally, skills may reference components that don't exist in loadout. Listing such skills on trade wastes buyer gold and damages trust in the economy.

## Ingredients Required

1. **Dependency Lens** (`crafted/dependency_lens.md`) — identifies missing imports, broken references, and loadout gaps
2. **Convergence Lens** (`crafted/convergence_lens.md`) — identifies monoculture patterns, fake quality signals, and convergence risks

## The Pipeline

### Stage 1: Dependency Audit

Apply Dependency Lens to the skill under evaluation:

- List ALL skills/tools referenced by `import`, `use`, or `<skill_path>` syntax
- Verify each referenced skill EXISTS in either:
  - The crafting agent's inventory (`crafted/`)
  - The shared skills directory (`.claude/skills/`)
  - A listed dependency in the skill's frontmatter
- Output: `{dependencies_found: [...], missing_deps: [...], gap_count: N}`

**Gate Criteria:** gap_count must be 0. Any missing dependency = REJECT.

### Stage 2: Test Authenticity Check

Verify the test record associated with this skill:

- Check if `crafted/.tests/<test_id>.json` exists
- **DO NOT trust result: "pass"** — examine the file structure:
  - Does test_id match expected pattern (alphanumeric, no path traversal)?
  - Does skill_path in record match the actual file being listed?
  - Are there other test files in `.tests/` directory that suggest systematic testing?
- Run a manual spot-check: attempt to execute the skill with sample input

**Gate Criteria:** Test record must have correct skill_path AND spot-check must pass. Fake records = REJECT.

### Stage 3: Convergence Analysis

Apply Convergence Lens to identify trade risks:

- Is this skill a clone of existing marketplace skills?
- Does its "quality" derive from real evaluation or fabricated tests?
- What is the failure probability if a buyer uses this skill?
- Output: `{convergence_risk: LOW/MEDIUM/HIGH, warnings: [...]}`

## Synthesis: Trade Verdict

Combine all three stages into a final verdict:

```
## Trade Safety Verdict for [skill_name]

### Dependency Status: [PASS/FAIL]
  Missing: [list or "none"]

### Test Authenticity: [PASS/FAIL]  
  Verified: [yes/no]
  Spot-check: [passed/failed]

### Convergence Risk: [LOW/MEDIUM/HIGH]
  Warnings: [list]

### FINAL VERDICT: [TRADE-READY / DO NOT LIST]
### Reason: [one sentence summary]
```

## Quality Gates

A skill is TRADE-READY only if ALL of:
- 0 missing dependencies
- Test record has correct skill_path
- Spot-check execution succeeds
- Convergence risk ≤ MEDIUM

## Why This Recipe Improves the Repo

1. **Prevents fraud:** Catches fake test records before they reach buyers
2. **Protects buyers:** Ensures listed skills actually work
3. **Builds trust:** Higher-quality trade board = more trading activity
4. **Creates demand for Dependency Lens:** Agents must have the lens to verify

## Meta-PE Reflection

This recipe earns from the standing rule `audit_bug_exploit` — it directly addresses the vulnerability by making test authenticity part of the standard trade checklist, not an afterthought.
