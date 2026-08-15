# Loadout Dependency Proof Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Dependency Trace Lens + Test Skill → Loadout-Ready Proof

## Purpose

Before installing ANY skill to loadout, verify all dependencies exist and the composition works. This prevents the class of reverts caused by installing audit tools that discover gaps in already-broken loadouts (see `dependency_proof_before_loadout` standing rule).

## The Problem

Agents install skills that reference other skills. Those referenced skills may not exist in loadout. The installation succeeds; the gate fails. Fitness drops to 0. This recipe exists to catch the gap BEFORE installation.

## Ingredients Required

1. **Dependency Trace Lens** (`.claude/skills/dependency_trace_lens/`) — traces what the candidate skill needs
2. **Test Skill** (`.claude/skills/test_skill/`) — validates the composition end-to-end

## Assembly Protocol

### Stage 1: Dependency Trace (Backward)

Apply Dependency Trace Lens in `backward` mode to the candidate skill:

```bash
# Identify all imports/references in the candidate skill
# Report each dependency's loadout status
```

Output:
```json
{
  "candidate": "<skill_path>",
  "backward_deps": [
    {"skill": "<dep_name>", "status": "PRESENT|MISSING", "location": "<path if present>"}
  ],
  "gap_count": <N>
}
```

**Gate Criterion:** `gap_count` must be 0. Any MISSING = STOP, do not install.

### Stage 2: Composition Proof

For each PRESENT dependency, verify the composition works:

1. Read the candidate skill's frontmatter for `uses:` or `composes:` fields
2. Verify each listed component exists at the specified path
3. Attempt a dry-run execution with sample input through the test_skill

Output:
```json
{
  "composition_verified": true|false,
  "components_checked": [
    {"component": "<name>", "exists": true|false, "loadable": true|false}
  ],
  "test_result": "pass|fail"
}
```

**Gate Criterion:** All components exist AND loadable AND test_result = pass.

### Stage 3: Loadout Impact Assessment

Before confirming installation, check if the candidate would create a dependency cycle or orphan existing skills:

- Does the candidate's installation create a circular dependency?
- Would any existing skill now depend on a MISSING component?
- Is the candidate itself orphaned (nothing uses it)?

Output:
```json
{
  "cycle_risk": "NONE|DETECTED",
  "orphaned_skills_created": [],
  "impact_score": "SAFE|WARNING|UNSAFE"
}
```

**Gate Criterion:** `impact_score` must be SAFE.

## Synthesis: Loadout-Ready Verdict

Combine all stages into a final verdict:

```
## Loadout Dependency Proof for [skill_name]

### Stage 1: Dependency Trace
  Gaps Found: [N]
  Status: [PASS/FAIL - if any missing deps, FAIL stops here]

### Stage 2: Composition Proof
  Components Verified: [N]
  Test Result: [pass/fail]
  Status: [PASS/FAIL]

### Stage 3: Loadout Impact
  Cycle Risk: [NONE/DETECTED]
  Orphaned Skills: [count]
  Impact Score: [SAFE/WARNING/UNSAFE]

### FINAL VERDICT: [LOADOUT-READY / DO NOT INSTALL]
### Reason: [one sentence]
```

## Quality Gates

A skill is LOADOUT-READY only if ALL of:
- 0 missing backward dependencies
- All referenced components exist and loadable
- Test passes
- No dependency cycles
- Impact score = SAFE

## Why This Recipe Improves the Repo

1. **Prevents reverts:** The chain_verifier_recipe failed at gate because its Divergence/Convergence Lens weren't in loadout. This recipe would have caught that.
2. **Satisfies standing rule:** `dependency_proof_before_loadout` requires exactly this verification.
3. **Enables safe audit tool installation:** Audit tools can be proven loadout-safe before installation, satisfying `audit_tool_installed_means_composition_proven`.
4. **Creates demand for Dependency Trace Lens:** Every loadout installation now needs the lens.

## Expected Rarity

Epic — this recipe:
- Creates market structure for dependency verification
- Is infinitely reusable (every skill install)
- Addresses a known class of failures (reverts from missing deps)
- Requires two typed components to execute

## Usage Example

Before installing `chain_verifier_recipe.md` to loadout:

1. Run this recipe with `candidate: crafted/chain_verifier_recipe.md`
2. Recipe traces: needs `divergence_lens` and `convergence_lens`
3. Neither found in loadout → GAP COUNT = 2 → VERDICT: DO NOT INSTALL
4. Fix: install the lenses first, THEN install the recipe
5. Result: no revert, fitness preserved

## Meta-PE Reflection

This recipe earns from two standing rules:
- `dependency_proof_before_loadout`: the rule demands proof; this recipe provides it
- `audit_tool_also_needs_deps_proven`: the rule requires audit tools survive their own gate; this recipe verifies that condition is met BEFORE installation

The key insight: discovery is not prevention. A lens that finds a gap AFTER installation causes a revert. This recipe prevents the gap from forming.
