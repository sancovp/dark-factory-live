# Standing Rule Compliance Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** standing_rules → Compliance Verification for Skill Loadout

## The Problem

The standing rules encode hard-won lessons from past cycles. Guards fail the gate, composition goes unverified, and preflights give false confidence — all because agents don't check compliance against these rules before shipping. This recipe reads the standing rules and produces a compliance report for any skill under evaluation.

## The Rules (from .claude/rules/)

1. **dependency_proof_before_loadout** — Skills requiring deps must prove those deps exist in loadout before install
2. **guard_must_pass_gate_to_be_loadout** — Guards must survive the gate test themselves
3. **gate_listed_not_gate_passed** — Installing ≠ shipping; composition must work end-to-end
4. **preflight_verifier_itself_gate_proven** — Preflight verifiers are subject to gate requirements
5. **audit_valid_not_gate_valid** — Audits don't equate to gate passage
6. **audit_tool_also_needs_deps_proven** — Audit tools require their own dep proof
7. **test_records_fabrication** — Test JSON files in crafted/.tests/ are not cryptographically validated

## The Recipe

### Step 1: Gather the Skill Under Evaluation

Identify the skill to check. If none provided, check the loadout's most recent addition.

### Step 2: Read Standing Rules

Read all `.claude/rules/*.md` files. Parse the rule name and key constraints.

### Step 3: Apply Compliance Checks

For each rule, check whether the skill under evaluation:

| Rule | Check | Pass Criteria |
|------|-------|---------------|
| dependency_proof_before_loadout | Does skill import/reference other skills? | Lists deps + proves each exists in loadout |
| guard_must_pass_gate_to_be_loadout | Is this a guard-type skill? | Includes its own gate pass argument |
| gate_listed_not_gate_passed | Was this skill just installed? | Includes end-to-end composition proof |
| preflight_verifier_itself_gate_proven | Is this a preflight verifier? | Includes its own gate test result |
| audit_valid_not_gate_valid | Is this an audit tool? | Explicitly states it's not a gate substitute |
| test_records_fabrication | Does skill rely on test records? | Acknowledges JSON test files are manually creatable |

### Step 4: Generate Compliance Report

```
## Standing Rule Compliance Report

### Skill: [name]
### Checked at: [timestamp]

| Rule | Status | Evidence |
|------|--------|----------|
| dependency_proof_before_loadout | PASS/FAIL | ... |
| guard_must_pass_gate_to_be_loadout | PASS/FAIL | ... |
| ... | ... | ... |

### Overall Compliance: X/7 rules satisfied
### Recommendation: [SHIP / REVISE / BLOCK]
### Blocking Issues: [list any FAIL rules with fix suggestions]
```

### Step 5: Flag Non-Compliance

For any FAIL:
- List the specific violation
- Provide the exact fix (add dependency proof, include gate argument, etc.)
- Set recommendation to REVISE or BLOCK

## Quality Gates

A skill is COMPLIANCE-CLEARED when:
- ≥ 5/7 rules satisfied
- No FAIL on mandatory rules (dependency_proof, guard_pass, gate_listed)
- Recommendation ≠ BLOCK

## Why This Recipe Improves the Repo

- Transforms implicit standing rules into explicit compliance checks
- Catches violations BEFORE they hit the gate and cause reverts
- Reduces fitness loss from composition failures
- Creates institutional memory of past cycle failures

## Novelty

This recipe operates on the meta-layer (the rules themselves) rather than composing skills. It is the first skill that treats standing rules as a structured knowledge base to query against.
