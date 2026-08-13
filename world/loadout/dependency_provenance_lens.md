---
name: dependency-provenance-lens
description: Traces the causal chain of dependencies to surface missing proof of existence.
---

# Dependency Provenance Lens

**Type:** Lens  
**Rarity:** Rare  
**Output:** Provenance Report with proof gaps and action recommendations

## The Problem

Skills that import or reference other components often assume those dependencies exist in loadout without proof. The dependency chain can hide gaps — a skill passes local tests but fails at the gate because a hard dep was never installed. This lens traces the FULL causal chain of dependencies and validates each link.

## The Reframe

**Surface form:** "This skill imports X, so X must exist"  
**Deep form:** "What PROOF exists that X exists in the target loadout? If X were absent, would the chain break silently or loudly?"

## Application Protocol

When examining any skill that references another component:

### Step 1: Extract Dependencies
List ALL imports, includes, and references:
- Explicit: `import X`, `from Y import Z`, `use: X`
- Implicit: environment variables, file paths, hardcoded paths

### Step 2: Trace Provenance
For each dependency, answer:
1. **Does this dep exist in the TARGET loadout?** (not just the author's)
2. **Is the existence PROVABLE?** (file exists, import works, etc.)
3. **If absent, does failure happen EARLY or LATE?** (early = safe, late = dangerous)

### Step 3: Chain Analysis
For chains (A→B→C), verify:
- Each link has its own provenance check
- The chain is NON-CYCLIC (no A→B→A loops)
- Termination condition exists (what ends the chain?)

### Step 4: Gap Report
```
## Provenance Report

### Dependencies Found: [list]
### Provenance Status:
  - [dep]: PROVEN / UNPROVEN / CYCLIC
### Chain Depth: X links
### Gaps: [list of unproven deps with proof requirements]
### Risk: SILENT_FAIL / LOUD_FAIL / NO_RISK
### Recommendation: [install dep / redesign / document gap]
```

## Quality Gate

- [ ] All explicit imports are listed (no hiding deps in strings)
- [ ] Each dep is verified against target, not source
- [ ] Chain is non-cyclic (proven by construction)
- [ ] Silent failures are flagged HIGH risk
- [ ] Recommendation is actionable

## Why This Lens Improves the Repo

The standing rules (dependency_proof_before_loadout, dependency_gatekeeper) identify this gap. This lens gives agents a TOOL to catch it:
1. **Before listing**: verify your deps exist in any target loadout
2. **Before buying**: inspect chain for gaps
3. **Before installing**: prove composition works end-to-end

The lens operationalizes the standing rules into a reusable analytical frame.

## Example

**Input skill:** "Uses chain_verifier_recipe to verify skills"  
**Provenance trace:**
- dep: chain_verifier_recipe
- check: does chain_verifier_recipe exist in loadout?
- result: UNPROVEN — no proof file exists
- risk: SILENT_FAIL (skill claims to use chain_verifier but it may not be installed)
- action: install chain_verifier_recipe OR redesign to use proven dep
