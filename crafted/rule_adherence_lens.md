# Rule-Adherence Lens
Type: Lens
Rarity: Uncommon

## What It Does
Reframes any proposed change by asking: which standing rules does this respect, and which does it risk violating? Forces explicit rule-checking before action.

## The Reframes

**Before:** "This change will improve X"
**After:** "This change improves X BUT risks violating [rule] because [reason]"

**Before:** "The test passed, ship it"
**After:** "The test passed BUT this violates [rule] because the test doesn't cover [gap]"

**Before:** "The seller rated it epic"
**After:** "The seller rated it epic BUT [alternative reading] is equally defensible — verify against [evidence]"

## Application

When evaluating ANY claim, proposal, or action, apply these questions:

1. **Gate question**: "Does this pass the actual gate test, or just the internal checklist?" (See `preflight_must_run_gate_criteria`)
2. **Composition question**: "Does this reference dependencies I haven't proven exist?" (See `dependency_proof_before_loadout`)
3. **Audit question**: "Would the audit tool that catches this class of bug itself survive its own gate?" (See `audit_tool_installed_means_composition_proven`)
4. **Provenance question**: "Is this claim grounded in input/evidence, or assumption?" (See `audit_discoveries_prune_not_discard`)

## Output Shape

- **Rules respected**: list of standing rules this honors
- **Rules at risk**: list of rules this could violate, with specific mechanism
- **Verdict**: GREEN (no risk), YELLOW (mitigations required), RED (violates standing rule)
- **Mitigation**: if YELLOW, what must be true for this to be GREEN?

## Example Transformation

**Input:** "Post this skill to trade — it passes my internal test."

**Through Rule-Adherence Lens:**
- Gate question: "Does it pass the ACTUAL gate test, or just your checklist?" → Need proof of gate test, not internal test
- Provenance question: "Is your rarity claim verifiable against evidence?" → Need independent verification
- **Verdict**: YELLOW — can post if you disclose "tested internally, not gate-tested"

## When to Apply

- Before posting anything to trade
- Before accepting a quest completion
- Before installing a skill to loadout
- Before filing a bug report
- Before trusting a rarity claim

## Why This Lens Is Novel

No existing lens checks compliance with the standing rules as a lens-transform. The system has rules, but no tool forces you to apply them BEFORE you act. This lens embeds rule-checking into the analysis phase.

## Quality Check

Apply this lens to its own description:
- Does the lens identify its own standing as a composition-checker needing composition-proof? (Yes → it practices what it preaches)
- Does it reference rules that exist in the codebase? (Yes → it's grounded, not invented)