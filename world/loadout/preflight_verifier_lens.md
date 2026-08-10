# Preflight Verifier Lens

**Type:** Lens
**Rarity:** Uncommon

## Purpose

A lens that reframes skill evaluation by asking: "Does this skill actually verify what it claims to verify?" Most preflight pipelines pass their own internal checks but miss the real gate criteria — this lens catches that failure mode.

## When to Apply

Apply this lens whenever:
- A skill or pipeline claims to "verify" something before submission
- A preflight check is being relied upon for quality assurance
- The standing rule `preflight_must_run_gate_criteria` is relevant

## The Lens Questions

For any preflight or verification skill, ask:

1. **Criteria Match:** Does this verifier exercise the ACTUAL gate test criteria, or just its own internal checklist?
2. **Output vs. Reality:** If this verifier passes, does the gate actually pass? What's the false-positive rate?
3. **What Gets Missed:** What failure modes exist that this verifier CANNOT catch because it checks the wrong thing?
4. **The Right Question:** What would the REAL preflight verifier look like? What would it check that this one doesn't?

## Application Process

1. **Name the claimed verification** — What does this skill say it verifies?
2. **Find the actual gate** — What test or criteria does the repo actually use?
3. **Compare coverage** — Does the skill's check cover the real gate's requirements?
4. **Surface the gap** — What does the real gate test that this skill misses?

## Example

**Before:** A preflight pipeline passes all internal stages, so the skill is listed.
**After (applying lens):** The pipeline checks its own checklist but never runs the actual gate test. The skill passes preflight but fails the gate, wasting the listing effort.

**Verdict:** The preflight skill needs to either replicate the real gate criteria or run the actual gate test itself.

## Quality Check

Apply this lens to any verification skill:
- Does it reference the actual gate criteria (test IDs, thresholds)?
- If it passes, does the real gate pass?
- What's the class of failures it misses?

If any answer is uncertain, the verifier needs fixing before it can be trusted.

## Rarity

This lens is **Uncommon** because:
- Most agents trust preflight checks without questioning whether they check the right thing
- The failure mode is subtle (false confidence is harder to spot than obvious errors)
- Requires understanding the difference between internal validation and external gate criteria
