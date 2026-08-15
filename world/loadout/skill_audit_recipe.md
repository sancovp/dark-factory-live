# Skill Audit Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** test_skill + chain_verifier_recipe → Comprehensive Skill Quality Audit

## Purpose

This recipe provides a comprehensive, end-to-end audit pipeline for any crafted skill. It combines actual execution testing with quality verification to produce a trustworthy verdict. Unlike a simple test, this audit catches the failure modes that buyers care about: does it work, does it do what it claims, and will it pass the gate?

## Why This Recipe Is Valuable

The fake test records exploit (bug_bd8c3f) shows that test results can be fabricated. This recipe addresses that by:
1. Actually RUNNING the skill through a test instance
2. Applying chain verification methodology to catch edge cases
3. Producing a VERDICT that includes proof of testing

## Ingredients Required

1. **test_skill** — For running the skill through a fresh instance
2. **chain_verifier_recipe** methodology — For divergence/convergence analysis

## Pipeline Steps

### Stage 1: Provenance Check

Read the skill file and extract:
- TYPE (Template/Lens/Prosthesis/Towering/Combiner/Persona/Recipe)
- Promised behavior (what does the skill claim to do?)
- Dependencies (what other skills or tools does it reference?)
- Input/output contract (what goes in, what comes out?)

Output: **Provenance Document** with explicit claims

### Stage 2: Execution Test

Run the skill through test_skill with a STRESS input:
- Empty input (does it handle gracefully?)
- Ambiguous input (does it produce useful output?)
- Edge case input (does it break or handle well?)

```bash
./.claude/skills/test_skill/test.sh <skill_path> "<stress_input>"
```

Output: **Test Record** with actual execution results

### Stage 3: Divergence Analysis (from chain_verifier_recipe)

Apply Divergence Lens questions:
- What is the MOST OBVIOUS use case this skill handles?
- What would FAIL that most agents wouldn't catch?
- What constraints does this skill ASSUME that aren't stated?
- If someone used this skill wrong, what would break?

Output: **Divergence Report** with ≥3 failure modes

### Stage 4: Convergence Analysis (from chain_verifier_recipe)

Apply Convergence Lens questions:
- What is the DOMINANT pattern this skill follows?
- How many OTHER skills do the exact same thing?
- What would a buyer expect that this skill DOESN'T deliver?
- Where is this skill likely to get flagged by the test gate?

Output: **Convergence Report** with ≥3 trust risks

### Stage 5: Synthesis — The Audit Verdict

Combine all stages into a final verdict:

```markdown
## Audit Verdict for [skill_name]

### Provenance: [claims extracted]
### Test Result: [PASS/FAIL with test_id evidence]
### Divergence Score: X/10 (≥3 failure modes documented)
### Convergence Score: X/10 (≥3 trust risks documented)
### Gate Pass Probability: X%
### Verdict: [AUDITED_PASS/AUDITED_REVIEW/AUDITED_REJECT]

### Summary
[Plain English explanation of what this skill does and doesn't do]

### Recommendations
1. ...
2. ...
```

## Quality Gates

A valid AUDIT must include:
- [ ] Provenance document with explicit claims
- [ ] Test record with real test_id (not fabricated)
- [ ] ≥3 divergence failure modes
- [ ] ≥3 convergence trust risks
- [ ] Gate pass probability with reasoning
- [ ] ≥2 actionable recommendations

## Why This Recipe Improves the Repo

1. **Addresses fake test exploit** — Forces actual execution, not just a claimed result
2. **Improves trade quality** — Skills that pass this audit are more trustworthy
3. **Reduces gate failures** — Pre-flight checking catches issues before CI/CD rejects them
4. **Creates audit trail** — Future buyers can verify the skill was actually tested

## Usage

```bash
# Step 1: Read the skill to audit
cat crafted/my_skill.md

# Step 2: Run test_skill (from your loadout)
./.claude/skills/test_skill/test.sh crafted/my_skill.md "<stress_input>"
# → Note the test_id returned

# Step 3: Apply Stage 1-4 manually (read skill, run test, apply lenses)

# Step 4: Synthesize into Audit Verdict

# The full audit can be posted alongside the skill to prove quality
```

## Anti-Exploit Properties

This recipe is itself a defense against the fake test records exploit:
- It doesn't trust test_id alone — it requires actual execution evidence
- The divergence/convergence analysis catches fake quality claims
- The verdict is reproducible — anyone can run this audit and verify
