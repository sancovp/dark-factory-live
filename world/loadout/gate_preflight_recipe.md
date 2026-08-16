# gate_preflight_recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** loadout_dependency_proof_recipe + chain_verifier_recipe + test_skill → Complete Gate-Ready Skill Verifier

## Purpose

Before any skill enters the trade economy or claims gate-ready status, verify it will survive the CI/CD gate. This recipe performs a three-stage preflight check: dependency proof, quality chain analysis, and actual execution test.

## The Problem

The standing rules (`gate_listed_not_gate_passed`, `dependency_proof_before_loadout`) establish that:
1. Listing a skill ≠ passing the gate
2. Dependencies must exist before claiming loadout-ready
3. A preflight that fails its own gate tanks fitness to 0

Most skills are listed without this triple check. This recipe enforces all three.

## Ingredients

1. **loadout_dependency_proof_recipe** — Verifies all referenced skills exist in loadout before the skill is trusted
2. **chain_verifier_recipe** — Applies Divergence + Convergence analysis to catch failure modes before the gate runs
3. **test_skill** — Actually executes the skill with sample input to verify real-world functionality

## The Pipeline

### Stage 1: Dependency Proof (loadout_dependency_proof_recipe)

```
Input: skill_path
Output: {dependencies_met: bool, missing_deps: [...], proof_score: N/10}
```

Apply the dependency proof recipe:
- List ALL imports, uses, and skill_path references
- Verify each exists in: crafted/, .claude/skills/, or listed in frontmatter deps
- Output: gap_count, missing_deps list, and proof_score

**Gate Criteria:** gap_count must be 0. Any missing dependency = FAIL (do not proceed).

### Stage 2: Chain Verification (chain_verifier_recipe)

```
Input: skill_path
Output: {divergence_score: N/10, convergence_score: N/10, gate_probability: N%, verdict: PASS/REVIEW/REJECT}
```

Apply the chain verifier:
- Run Divergence Lens: find 3+ failure modes the skill misses
- Run Convergence Lens: find 3+ trust risks from monoculture patterns
- Compute gate pass probability with reasoning
- Output: Chain Verdict with specific recommendations

**Gate Criteria:** Gate probability must be ≥ 70% AND verdict must be PASS or REVIEW. REJECT = FAIL.

### Stage 3: Execution Test (test_skill)

```
Input: skill_path, sample_input
Output: {executed: bool, output: string, error: string|null}
```

Actually run the skill through a fresh Claude instance:
- Execute with representative sample input
- Capture output and any errors
- Verify output matches expected structure

**Gate Criteria:** executed must be true AND error must be null. Execution failure = FAIL.

## Synthesis: Gate Preflight Verdict

Combine all three stages into a final verdict:

```markdown
## Gate Preflight Verdict for [skill_name]

### Stage 1: Dependency Proof
- Status: [PASS/FAIL]
- Missing deps: [list or "none"]
- Proof score: [N/10]

### Stage 2: Chain Verification
- Status: [PASS/FAIL]
- Divergence score: [N/10]
- Convergence score: [N/10]
- Gate probability: [N%]
- Verdict: [PASS/REVIEW/REJECT]

### Stage 3: Execution Test
- Status: [PASS/FAIL]
- Executed: [yes/no]
- Error: [none or description]

### FINAL VERDICT: [GATE-READY / NOT GATE-READY]
### Reason: [one sentence summary]
### Fitness Impact: [improves/neutral/harms]
```

## Quality Gates

A skill is GATE-READY only if ALL of:
- Stage 1: 0 missing dependencies (gap_count = 0)
- Stage 2: gate_probability ≥ 70% AND verdict ∈ {PASS, REVIEW}
- Stage 3: executed = true AND error = null

## Why This Recipe Improves the Repo

1. **Enforces standing rules:** Directly implements `gate_listed_not_gate_passed` and `dependency_proof_before_loadout`
2. **Prevents fitness loss:** Skills verified by this recipe won't cause the 0-fitness revert
3. **Improves throughput:** Fewer gate failures = higher overall system throughput (currently at 20)
4. **Creates trust:** Trade board skills verified by this recipe can be trusted by buyers
5. **Addresses divergence:** By making all skills gate-ready, the economy stabilizes and trading resumes

## Meta-PE Reflection

This recipe earns from the meta-principle that compositions should create emergent capabilities impossible from parts alone. By chaining three distinct verification approaches (proof, analysis, execution), it creates a gate-ready certification that no single component provides. The novelty is in the COMBINATION, not the individual parts.
