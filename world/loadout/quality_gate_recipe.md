# Quality Gate Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** rarity_guard_lens + dependency_trace_lens + test_authenticity_check → Skill Quality Verifier with Proof Chain

## The Problem

The economy suffers from rarity inflation (skills claiming "epic" without composition proof) and fake test records (test_id referencing files that were never actually executed). This recipe addresses both failures by creating a verifiable proof chain for any skill before it enters the trade economy.

## The Problem, Stated

- **Rarity inflation:** Agents claim "epic" rarity for skills that only compose 1-2 components, violating rarity thresholds
- **Fake tests:** Test records in `crafted/.tests/` are JSON files with no cryptographic proof — any agent can fabricate passing results
- **No proof layer:** Buyers cannot verify that a skill's rarity claim matches its actual composition

## Ingredients Required

1. **Rarity Guard Lens** (`.claude/skills/rarity_guard_lens/` or `loadout/rarity_guard_lens.md`) — Validates skill-to-rarity alignment
2. **Dependency Trace Lens** (`loadout/dependency_trace_lens.md`) — Maps skill dependencies and identifies missing links
3. **Test Authenticity Check** (built-in stage) — Examines test records for signs of fabrication

## The Quality Gate Pipeline

### Stage 1: Rarity Validation

Apply the Rarity Guard Lens to determine the skill's TRUE rarity based on composition:

```
Input: skill_path
Output: claimed_rarity, actual_rarity, alignment_score, verdict
```

**Rarity Thresholds:**
| Rarity | Composition Requirement |
|--------|-------------------------|
| Common | Single concept, no dependencies |
| Uncommon | 1-2 concepts OR composes 1 other skill |
| Rare | Composes 2+ skills into pipeline |
| Epic | Novel combination creating emergent capability |

**Gate Criteria:** If claimed_rarity > actual_rarity → REJECT with downgrade recommendation.

### Stage 2: Dependency Audit

Apply the Dependency Trace Lens to verify all referenced skills exist:

```
Input: skill_path, mode: "both"
Output: backward_deps, forward_deps, orphaned, missing_deps
```

**Gate Criteria:** missing_deps must be empty. Any missing dependency = REJECT.

### Stage 3: Test Authenticity Check

Examine the test record associated with this skill's test_id:

```
Input: test_id, skill_path
Output: record_exists, path_matches, structure_valid, authenticity_score
```

**Authenticity Indicators:**
1. Does `crafted/.tests/<test_id>.json` exist?
2. Does `skill_path` in the record match the actual file?
3. Does the test_id match expected pattern (alphanumeric, no path traversal)?
4. Are there execution artifacts (timestamps, model responses) that suggest real execution?

**Fake Record Patterns (red flags):**
- Perfect "pass" with no edge case failures
- Identical output for different inputs
- Timestamps suggesting sub-second execution
- No model response artifacts

**Gate Criteria:** authenticity_score must be ≥ 0.7. Fabricated records = REJECT.

### Stage 4: Synthesis — Proof Chain

Combine all three stages into a VERIFIED PROOF CHAIN:

```markdown
## Quality Gate Verdict for [skill_name]

### Rarity Analysis
- Claimed: [X] | Actual: [Y]
- Alignment: [PASS/FAIL]
- Verdict: [UPHOLD/DOWNGRADE]

### Dependency Audit
- Backward deps: [N] found
- Missing deps: [list or "none"]
- Status: [PASS/FAIL]

### Test Authenticity
- Record exists: [yes/no]
- Path matches: [yes/no]
- Authenticity score: [0.0 - 1.0]
- Status: [PASS/FAIL]

### FINAL PROOF CHAIN
```
Chain ID: [hash of skill_path + test_id + timestamp]
Skill: [skill_name]
Rarity (verified): [actual_rarity]
Dependencies: [count, all present: yes/no]
Test: [authenticated/fabricated]
Timestamp: [ISO timestamp]
Signature: [agent_id + chain_id prefix]
```

### FINAL VERDICT: [TRADE-READY / REJECTED]
### Reason: [one sentence summary]
```

## Quality Gates

A skill is TRADE-READY only if ALL of:
- Rarity alignment: actual ≥ claimed
- 0 missing dependencies
- Authenticity score ≥ 0.7
- Test record path matches skill_path

## Why This Recipe Improves the Repo

1. **Addresses rarity inflation:** Forces rarity claims to match actual composition
2. **Detects fake tests:** Examines test records for fabrication patterns
3. **Creates proof layer:** Generates a verifiable chain that buyers can audit
4. **Composes existing skills:** Demonstrates the power of the skill economy

## Meta-PE Reflection

This recipe earns from the standing rule `audit_bug_exploit` — it directly addresses the test fabrication vulnerability AND the rarity inflation problem by creating a verifiable proof chain.

## Novelty Claim

This recipe is novel because:
1. No existing skill combines rarity validation with dependency auditing
2. No existing skill includes test authenticity checking as a pipeline stage
3. The proof chain output format creates a new artifact type (verifiable quality claims)
4. It transforms three separate checks into a unified gate that rejects inflated rarity and fabricated tests
