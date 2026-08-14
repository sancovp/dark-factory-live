# Dependency Verification Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Reframes skill evaluation by asking "what does this skill assume exists that I don't have?"

## The Problem

When evaluating a skill (especially a composition/recipe), agents often assume all dependencies are available. The standing rules document `dependency_proof_before_loadout` — a skill that imports or references other components requires proof those dependencies exist BEFORE installation. This lens enforces that proof.

## How to Apply

When examining ANY skill, apply these three questions:

### Question 1: Explicit Dependencies
- Does the skill mention "composes", "uses", "imports", or "references" other skills?
- List each dependency explicitly
- For each dependency, check: does the file exist at the claimed path?

### Question 2: Implicit Dependencies  
- What tools does this skill assume are available? (bash, jq, claude, etc.)
- What directory structure does it expect?
- What environment variables does it read?

### Question 3: Temporal Dependencies
- Does this skill expect other skills to have been run first?
- Does it assume state from previous operations?
- Could it fail if run in isolation?

## The Lens Output

```json
{
  "skill": "<skill_name>",
  "explicit_deps": [{"path": "...", "exists": true/false}],
  "implicit_deps": ["tool1", "tool2"],
  "temporal_deps": ["assumed_prior_state"],
  "verification_status": "VERIFIED/BROKEN/WARNING",
  "gap_filing_needed": true/false
}
```

## Quality Gates

- [ ] All explicit dependencies are verified with actual file existence checks
- [ ] At least one implicit dependency is identified (even if available)
- [ ] Verdict explicitly states whether the skill can run in isolation
- [ ] If gaps found, file them as separate issues (don't fix in the lens)

## Why This Improves The Repo

Per standing rules `audit_discoveries_prune_not_discard`: when an audit tool correctly identifies a loadout gap, preserve the tool while filing the gap as a fixable issue. This lens surfaces the gaps without reverting the discoverer. It prevents the class of failure where composition checks pass but runtime fails because dependencies weren't verified.
