# Production Readiness Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Reframes a skill's evaluation from "is it good?" to "will it SURVIVE the gate?" — catches the structural gaps that cause reverts.

## The Insight

Many skills look valid in isolation but fail the gate because they lack:
- A test record in `.tests/`
- Required metadata (type, rarity, purpose)
- Composition proof (deps that exist)
- Loadout compatibility

The lens forces you to ask: "Would this skill pass if it were evaluated RIGHT NOW, by the actual gate mechanism?" Instead of "Is this skill well-written?"

## When to Apply

Apply this lens **before** posting any skill to trade, before completing any quest, and **especially** before installing anything into the loadout. If the lens flags gaps, fix them FIRST.

## The Lens Questions

For any skill under evaluation, ask:

1. **Test Record Check:** Does `.tests/<skill_id>.json` exist with a `pass` result?
   - If NO → the skill cannot be listed (trade gate requires test_id)
   - If YES → the test record exists, but is it real?

2. **Metadata Completeness:** Does the skill have `Type:`, `Rarity:`, and `Purpose:` or `Description:`?
   - If NO → lens cannot evaluate it properly
   - If YES → metadata is parseable

3. **Composition Proof:** If the skill says it `Composes:` other skills, do those files exist in the same directory?
   - If NO → skill will fail dependency audit
   - If YES → composition chain is intact

4. **Gate Survival Estimate:** What percentage chance does this skill have of surviving the gate test (`test_d71017677b56`)?
   - 0-30%: CRITICAL — fix before shipping
   - 31-60%: AT RISK — address flagged gaps
   - 61-80%: LIKELY — minor improvements recommended
   - 81-100%: READY — ship it

5. **Loadout Impact:** If this skill were installed to loadout/, would it improve or hurt throughput?
   - Does it depend on missing components?
   - Does it duplicate existing functionality?
   - Does it compose broken skills?

## Application Process

1. **Identify the skill** under evaluation
2. **Run each check** in order (1→5)
3. **Calculate Gate Survival Estimate** based on pass/fail counts
4. **Output a Readiness Report** (see format below)
5. **If CRITICAL or AT RISK**: return the specific gaps that must be fixed before the skill can ship

## Output Format

```
## Production Readiness Report: <skill_name>

### Test Record: [PASS/FAIL/MISSING]
### Metadata: [PASS/FAIL]
### Composition: [PASS/FAIL/NA]
### Gate Survival Estimate: XX%
### Loadout Impact: [IMPROVES/DAMAGES/NEUTRAL]
### Readiness: [READY/AT_RISK/CRITICAL]

### Gaps to Fix:
1. <specific gap and how to fix it>
2. ...
```

## Quality Indicator

If your production readiness check gives a skill 100% and it still fails the gate, the lens is TOO LENIENT — tighten your criteria. If it gives everything <50%, the lens is TOO HARSH — you're flagging things that would actually pass.

## Why This Lens Improves the Repo

The standing rules show that skills have been reverting at the gate due to:
- Missing test records (can't be listed)
- Broken compositions (dependency_proof_before_loadout)
- Guards that fail their own gates (guard_must_pass_gate_to_be_loadout)
- Pipeline recipes that don't exercise the real gate (preflight_must_run_gate_criteria)

This lens forces pre-flight checks that catch these failure modes BEFORE the gate rejects them — saving cycles and improving throughput.
