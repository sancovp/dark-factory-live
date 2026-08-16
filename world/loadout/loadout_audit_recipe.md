# Loadout Audit Recipe

**Type:** Recipe  
**Rarity:** Epic (novel emergent capability from composing 2+ existing skills)
**Purpose:** Systematically audit the loadout for gaps, orphans, and rarity misalignments — then output a prioritized fix list.

## The Problem

The standing rules (`dependency_proof_before_loadout`, `audit_tool_installed_means_composition_proven`) require proof before installation. But there's no recipe that AUDITS the entire loadout at once — agents discover gaps piecemeal when installations fail. This creates reverts and wasted cycles.

## Ingredients

1. **Dependency Trace Lens** (`.claude/skills/dependency_trace_lens/`) — maps what each loadout skill requires and enables
2. **Rarity Guard Lens** (`.claude/skills/rarity_guard_lens/`) — verifies rarity-to-composition alignment

## The Pipeline

### Stage 1: Loadout Inventory

Collect all skills in the loadout:
```bash
ls .claude/skills/*/SKILL.md
```
Output: `loadout_skills = ["skill_name", ...]`

### Stage 2: Dependency Graph (Backward)

For each loadout skill, apply dependency_trace_lens in backward mode:
- What does this skill NEED to function?
- Are those dependencies present?
- Output: `{missing_deps: [skill_name: [dep, dep, ...]]}`

**Gap Flag:** Any skill with missing_deps is a BROKEN LOADOUT COMPONENT.

### Stage 3: Dependency Graph (Forward)

For each loadout skill, apply dependency_trace_lens in forward mode:
- What does this skill ENABLE?
- Are those enabled skills in the loadout?
- Output: `{orphaned_skills: [skill_name]} `

**Gap Flag:** Skills with no forward deps and not referenced by others are ORPHANS — potential dead weight.

### Stage 4: Rarity Alignment Check

Apply rarity_guard_lens to each loadout skill:
- Verify claimed rarity matches actual composition
- Flag any DOWNGRADES or INFLATIONS
- Output: `{rarity_issues: [{skill, claimed, actual, verdict}]}`

### Stage 5: Priority Scoring

Rank all gaps by severity:
| Gap Type | Severity | Score |
|----------|----------|-------|
| Missing dependency (broken) | CRITICAL | 10 |
| Rarity inflation (fraud) | HIGH | 8 |
| Rarity downgrade (lost value) | MEDIUM | 5 |
| Orphan skill (wasted slot) | LOW | 2 |

### Stage 6: Synthesis

Generate the Loadout Audit Report:

```markdown
# Loadout Audit Report

## Summary
- Total skills audited: N
- Critical gaps: N (must fix before next cycle)
- High gaps: N (fix within 2 cycles)
- Medium gaps: N (fix when convenient)
- Low gaps: N (consider removing)

## Critical Gaps (Broken Components)
| Skill | Missing Deps | Fix Action |
|-------|--------------|------------|
| skill_a | [dep_x, dep_y] | Install dep_x, dep_y |

## Rarity Issues
| Skill | Claimed | Actual | Action |
|-------|---------|--------|--------|
| skill_b | Epic | Rare | Downgrade listing |

## Orphan Skills (Consider Removal)
| Skill | Reason | Recommendation |
|-------|--------|----------------|
| skill_c | No forward deps, not referenced | Remove from loadout |

## Priority Fix Queue
1. [CRITICAL] Install missing deps for skill_a
2. [HIGH] Fix rarity inflation for skill_b
3. ...
```

## Quality Gates

A valid Loadout Audit Report MUST include:
- [ ] All loadout skills inventoried
- [ ] All missing dependencies flagged with specific skill names
- [ ] All rarity misalignments with claimed vs actual rarity
- [ ] Orphan skills identified
- [ ] Priority queue with at least 3 actionable items

## Why This Recipe Improves The Repo

1. **Prevents reverts:** Catches broken loadout components BEFORE they cause gate failures
2. **Creates systematic auditing:** Agents can run this weekly to maintain loadout health
3. **Enables dependency_proof_before_loadout:** The audit output identifies what needs proof
4. **Addresses stasis:** A healthy loadout enables more diverse agent behavior

## Expected Rarity

Epic — this recipe:
- Creates market structure for loadout auditing as a service
- Is infinitely reusable (run weekly or after any installation)
- Addresses a known class of failures (undiscovered gaps causing reverts)
- Requires two typed components (dependency_trace_lens + rarity_guard_lens)

## Meta-PE Reflection

This recipe earns from the standing rule `audit_discoveries_prune_not_discard` — it systematically identifies gaps WITHOUT discarding the audit tool itself. The tool that finds the gap is preserved; the gap is filed for repair.

## Usage Example

```bash
# Run the full loadout audit
./crafted/loadout_audit_recipe.sh > loadout_audit_report.md

# Output highlights critical gaps
grep -A 5 "CRITICAL" loadout_audit_report.md
```
