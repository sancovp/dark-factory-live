# loadout_gap_lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Identify missing capabilities in the current loadout by analyzing gaps between what skills exist and what the repo actually needs.

## The Problem

Standing rules (`dependency_proof_before_loadout`, `audit_tool_also_needs_deps_proven`) establish that loadout gaps cause revert cascades. The loadout_dependency_proof_recipe catches missing dependencies AFTER a skill is built — this lens finds the MISSING capabilities BEFORE they become gaps.

## How to Use This Lens

Apply to the current loadout to answer: "What skills SHOULD exist but DON'T?"

## The Lens Questions

For each skill category in the repo, ask:

1. **Does the loadout have a dependency verifier?** (proves composition)
2. **Does it have a chain verifier?** (applies divergence + convergence)
3. **Does it have a trade safety checker?** (authenticates test records)
4. **Does it have a gate preflight pipeline?** (executes before listing)
5. **Does it have a divergence corrector?** (rebalances economy)

## Gap Analysis Output

```
## Loadout Gap Analysis

### Categories Present: [list]
### Categories Missing: [list]
### Gap Severity: [none/low/medium/high/critical]

### Recommendations:
1. [What to build next]
2. [Why it fills a critical gap]
```

## Severity Scale

| Severity | Condition | Action |
|----------|-----------|--------|
| none | All 5 categories present | Loadout is complete |
| low | 4/5 present, 1 unused | Monitor |
| medium | 3/5 present | Build missing within 2 rounds |
| high | 2/5 present | Priority build |
| critical | ≤1 present | Immediate intervention |

## Example Application

Apply to this loadout:
- dependency_proof_recipe → ✓
- chain_verifier_recipe → ✓
- trade_safety_recipe → ✓
- gate_preflight_recipe → ✓
- divergence_corrector_recipe → ✓

**Result:** none severity — loadout is complete.

## Why This Lens Improves the Repo

1. **Prevents revert cascades:** Find gaps before they cause fitness loss
2. **Guides skill development:** Shows what to build next
3. **Enforces standing rules:** Directly addresses `dependency_proof_before_loadout`
4. **Creates selection pressure:** Identifies where new skills are most valuable
