# Dependency Proof Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Reframes skill evaluation to catch dependency_proof_before_loadout violations

## The Problem This Lens Addresses

The standing rules codify a critical constraint: a skill that IMPORTs or REFERENCEs other components requires PROOF those dependencies exist in loadout BEFORE installation. This is not optional — it's a hard dependency gate.

Yet without systematic tooling, agents can:
1. Craft a skill that references `Divergence Lens`
2. Install it to loadout
3. Have the gate catch the missing dependency — costing fitness
4. Revert with zero improvement

The Dependency Proof Lens makes this class of failure visible BEFORE the gate catches it.

## How to Apply This Lens

Before evaluating ANY skill for loadout fitness, apply this lens:

### Step 1: Identify the Skill's Explicit Dependencies

Read the skill file and find ALL references to other skills, components, or tools. Look for:
- "Use [Skill Name]" or "Apply [Lens Name]"
- "Requires: [component]"
- "Import from [path]"
- "Reference: [skill]"
- Any action verb that presupposes another artifact exists

Output: **Dependency List** — e.g., `"Divergence Lens", "Convergence Lens", "test_skill"`

### Step 2: Verify Each Dependency Exists in Loadout

For each dependency identified in Step 1:
1. Check if it exists in the agent's `.claude/skills/` directory
2. Check if it exists in `loadout/` (if loadout is separate)
3. Check if it's in the marketplace/plugin pool

Output: **Dependency Audit** — mark each as FOUND or MISSING

### Step 3: Check for Proof of Composition

For audit tools, verifiers, gatekeepers, and chainers (these have elevated requirements):
1. Does the skill's own hard dependencies exist in loadout?
2. Has the skill passed its own gate test?
3. Is there documentation of the dependency chain?

Output: **Composition Proof Status** — PROVEN, UNPROVEN, or N/A

### Step 4: Render the Dependency Verdict

Combine the audits into a structured verdict:

```
## Dependency Proof Verdict for [skill_name]

### Explicit Dependencies Found: N
### Dependencies Verified in Loadout: M/N
### Missing Dependencies: [list or "None"]

### Lens Result: [PASS/FAIL]
- PASS: All dependencies exist and composition is proven (or N/A)
- FAIL: Any dependency missing OR composition unproven for audit-class skills

### Recommended Action:
- If PASS: Skill is dependency-safe for loadout
- If FAIL: Do NOT install; file the missing dependency as a tracked issue
```

## Key Questions This Lens Forces

1. **Does this skill assume something that doesn't exist?**
   - If yes → FAIL. Don't install. File the gap.

2. **Is this an audit/verifier/gatekeeper skill?**
   - If yes → Does it have its own deps proven?
   - A verifier that fails its own gate is worse than no verifier.

3. **Would this skill fail the gate due to a missing dependency?**
   - If yes → Catch it here, not at the gate.

4. **Can the missing dependency be easily resolved?**
   - If yes → Install the dependency first, then the skill.
   - If no → The skill is not loadout-ready.

## Why This Lens Improves the Repo

The standing rules codify dependency_proof_before_loadout, but:
- The rule exists in `.claude/rules/` — not applied at craft time
- The gate catches failures — this lens PREVENTS them
- Audit tools need extra scrutiny — this lens gives them extra scrutiny

By applying this lens before any skill evaluation:
1. Fewer skills revert at the gate (pre-flight check)
2. Fewer audit tools install into known-broken composition
3. Fitness stays stable (no drops from revert cycles)
4. The dependency chain becomes traceable

## Test: Apply This Lens to Itself

Apply this lens to `dependency_proof_lens.md` itself:
- Does it reference any other skills? → No (it's self-contained)
- Is composition proof needed? → N/A
- Does it pass its own standard? → YES

This lens passes its own lens — which is the only way to prove it's loadout-ready.
