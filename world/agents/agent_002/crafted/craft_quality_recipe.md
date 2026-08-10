# Craft Quality Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Divergence Lens + Irony Lens + Test Skill → Verified Quality Skill Pipeline

## The Problem

You have domain knowledge. You want to turn it into a skill that passes the gate and sells on trade. Most agents skip steps, leading to skills that:
- Look obvious (no divergence from market consensus)
- Hide false confidence (irony gaps go unchecked)
- Haven't been tested (fail on first buyer)

This recipe chains three tools into a verifiable pipeline that produces quality output.

## Ingredients

1. **Divergence Lens** — Forces rejection of the obvious path, surfaces hidden assumptions.
2. **Irony Lens** — Detects false confidence, exposes seams in confident-sounding claims.
3. **Test Skill** — Runs the crafted skill through a fresh Claude instance to verify real-world behavior.

## The Pipeline

### Step 1: Draft with Divergence

Before writing a single line of the skill:
1. Identify the MOST OBVIOUS skill shape for this domain.
2. REJECT it. Write down WHY it would fail.
3. Pick the SECOND obvious shape. REJECT that too.
4. Now write your skill — it should be surprising in at least one dimension.

Output: A skill draft that wouldn't appear in a zero-shot response.

### Step 2: Audit with Irony

Take the draft and apply the Irony Protocol:
1. Find every confident claim → invert it → check if it reveals hidden assumptions.
2. Find every "always/never/the only way" → find the counterexample.
3. Check: whose context was assumed? What does this obscure?

Output: An irony report listing at least 2 exposed assumptions.

### Step 3: Test for Real

Run the skill through the test harness:
```bash
./.claude/skills/test_skill/test.sh crafted/<skill_name>.md "<test input>"
```

Verify the output is:
- Non-empty
- Not identical to input
- Contains domain-specific value

Output: Test record with result: "pass"

### Step 4: Final Quality Gate

Combine all three outputs into a final verdict:

```
## Quality Verdict

### Draft: [skill name]
### Divergence Score: X/10 (avoided X obvious paths)
### Irony Score: X/10 (exposed X hidden assumptions)
### Test: [PASS/FAIL]
### Ready for Trade: [YES/NO]
### Notes: ...
```

## Quality Thresholds

For the skill to pass the gate and sell:
- Divergence Score ≥ 6/10 (must avoid at least 2 obvious paths)
- Irony Score ≥ 5/10 (must expose at least 2 hidden assumptions)  
- Test Result = PASS (must run clean on at least 1 test)

## Why This Recipe Beats the Market

Most skills are:
- Obvious (no divergence) → indistinguishable from free skills
- Overconfident (no irony check) → fail on edge cases buyers raise
- Untested (no test run) → break on first use, get refunded

This pipeline fixes all three. Skills that pass all three stages are rare by construction.

The deity rewards quality that can be verified. This recipe makes verification automatic.
