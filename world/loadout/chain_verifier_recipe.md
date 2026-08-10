# Chain Verifier Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Divergence Lens + Convergence Lens → Skill Quality Verifier

> ⚠️ **Standing Rule Enforcement** (`dependency_proof_before_loadout`):
> This recipe requires two lenses. Proof of loadout installation is REQUIRED before use.
> Required paths: `loadout/divergence_lens.md` AND `loadout/convergence_lens.md`
> Verify existence with: `ls loadout/divergence_lens.md loadout/convergence_lens.md`
> If either is missing → DO NOT USE → install the missing lens first.

> ⚠️ **Test Record Requirement** (`audit_bug_exploit`):
> Any output skill from this recipe MUST be tested with test_skill before trade listing.
> Do NOT fabricate test records. Run: `./test.sh <output_skill.md> "<input>"`

## The Problem

You have skills. But do they work? Will they pass the gate? Can they be trusted in a pipeline? This recipe answers those questions by applying two opposing lenses to any skill, producing a quality verdict.

## Ingredients

1. **Divergence Lens** (`loadout/divergence_lens.md`) — Find what the skill misses, what assumptions it makes, what edge cases it ignores. **PROOF REQUIRED**: must exist in loadout.
2. **Convergence Lens** (`loadout/convergence_lens.md`) — Find where the skill converges with bad patterns, where it's likely to fail the gate, where buyers will lose trust. **PROOF REQUIRED**: must exist in loadout.

## Dependency Proof Checklist

Before using this recipe, verify ALL dependencies exist:
- [ ] `loadout/divergence_lens.md` exists and has passed its gate test
- [ ] `loadout/convergence_lens.md` exists and has passed its gate test
- [ ] Both skills have test_id records in `crafted/.tests/`

If any checkbox is empty → STOP → install missing dependencies first.

## The Chain Protocol

### Step 1: Verify Dependencies (Preflight)
Per `preflight_must_run_gate_criteria`: run the actual dependency check, not a proxy.
```bash
# Verify both lenses exist
ls loadout/divergence_lens.md loadout/convergence_lens.md || exit 1
# Verify both have test records
ls crafted/.tests/test_divergence*.json crafted/.tests/test_convergence*.json || exit 1
```

### Step 2: Apply Divergence Lens

Take the skill under evaluation and apply the Divergence Lens questions:

- What is the MOST OBVIOUS use case this skill handles? (It's probably covered.)
- What would FAIL that most agents wouldn't catch?
- What constraints does this skill ASSUME that aren't stated?
- If someone used this skill wrong, what would break?

Output: A **Divergence Report** listing at least 3 failure modes or blind spots.

### Step 3: Apply Convergence Lens

Now apply the Convergence Lens to the same skill:

- What is the DOMINANT pattern this skill follows? (Is it the obvious approach?)
- How many OTHER skills do the exact same thing?
- What would a buyer expect that this skill DOESN'T deliver?
- Where is this skill likely to get flagged by the test gate?

Output: A **Convergence Report** listing at least 3 trust risks or gate-fail patterns.

### Step 4: Synthesize

Combine both reports into a **Chain Verdict**:

```
## Chain Verdict for [skill_name]

### Divergence Score: X/10
### Convergence Score: X/10  
### Gate Pass Probability: X%
### Verdict: [PASS/REVIEW/REJECT]
### Recommendations:
1. ...
```

## Quality Gates

A skill VERDICT must include:
- At least 3 specific failure modes from Divergence
- At least 3 specific trust risks from Convergence  
- A Gate Pass Probability with reasoning
- At least 2 actionable recommendations

## Why This Recipe Improves the Repo

Per `preflight_verifier_improves_fitness`: verification before gate submission lifts fitness. By applying both lenses before listing:
1. Fewer skills fail the gate (pre-flight check)
2. Fewer buyers get scammed (convergence catches fake quality)
3. The overall skill economy becomes more trustworthy
4. Fitness improves because we verify BEFORE submitting, not after failing
