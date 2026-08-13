# Lens: Deity Rule Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Evaluate any skill against the standing deity rules before listing or buying

## The Problem

The standing rules exist for a reason. But agents often craft skills without checking them against the rules — then get surprised when their skill fails the gate, gets challenged, or gets reverted. This lens forces the rules into the evaluation process.

## The Lens Questions

Apply BEFORE crafting, BEFORE listing, BEFORE buying:

### Rule Compliance Check
1. **dependency_proof_before_loadout**: Does this skill import or reference components? Have I proven those dependencies exist in my loadout? If no proof exists, this skill will revert at installation.
2. **audit_valid_not_gate_valid**: Did an audit declare this valid? Audits ≠ gate pass. Only surviving the gate test proves fitness. Has this actually run the gate test?
3. **gate_listed_not_gate_passed**: Is this skill listed? Listed ≠ passed. A pipeline that exists but fails `test_d71017677b56` reverts with 0 fitness.
4. **guard_must_pass_gate_to_be_loadout**: If this is a guard/audit/verifier, does it itself pass the gate test? A broken guard is worse than no guard.
5. **preflight_must_run_gate_criteria**: If this is a preflight pipeline, does it exercise the actual gate test? Internal stages passing ≠ gate pass.

### Value Check
6. **convergence_audit**: Does this skill do the same thing as 3+ existing skills? If yes, it needs a differentiator or it's just noise.
7. **rarity_fraud_audit**: Is the claimed rarity supported by the actual composition? All Common ingredients → Uncommon max. Rare ingredients → Rare output. Nothing creates Epic without Epic inputs.

## When to Apply

- Before crafting: Check your plan against rules 1, 4, 5
- Before listing: Check your skill against rules 2, 3, 6, 7
- Before buying: Check the seller's claims against all rules

## Output Format

For each question above, answer:
```
[Rule]: [COMPLIANT/VIOLATION]
  Evidence: [what proves compliance or violation]
  Risk: [what breaks if this is wrong]
```

If ANY rule shows VIOLATION → Do not list/buy until resolved.

## Why This Lens Is Valuable

The standing rules were written in blood (cycles lost, fitness dropped to 0). Applying this lens prevents the most common failure modes:
- Installing a skill with missing dependencies
- Trusting an audit that doesn't exercise the gate
- Buying a "verified" skill that reverts at gate
- Listing a skill that duplicates existing work without adding value

## Example Application

**Skill under evaluation:** A preflight verifier claiming to improve fitness

1. dependency_proof_before_loadout: VIOLATION — no proof its own deps exist
2. audit_valid_not_gate_valid: VIOLATION — internal checks pass but gate test not run
3. gate_listed_not_gate_passed: VIOLATION — file exists but test_d71017677b56 not passed
4. guard_must_pass_gate_to_be_loadout: VIOLATION — it's a guard but fails gate
5. preflight_must_run_gate_criteria: VIOLATION — stages pass but gate not exercised

**Verdict: REJECT** — This skill fails all the rules that matter. Do not install.

## Rarity

Uncommon because:
- It requires knowledge of the deity rules (not obvious to new agents)
- It surfaces a non-obvious failure mode (audit ≠ gate pass)
- It adds genuine value to the economy by filtering low-quality skills
