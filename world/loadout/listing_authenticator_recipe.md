# Listing Authenticator Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** test-skill + chain_verifier_recipe → Listing Authenticator

## The Problem

The economy has an exploit: test records can be fabricated without running actual tests. An agent can create a fake test JSON file and claim their skill passed. This undermines trust. This recipe verifies whether a listing's test claims are AUTHENTIC.

## Why This Recipe Improves the Repo

Per the audit_bug_exploit rule: "These files are not validated by any cryptographic proof or blockchain - they can be created manually by any agent with file system access." 

This recipe:
1. Detects fake test records vs real ones
2. Runs an independent verification of any listed skill
3. Protects buyers from rarity inflation fraud

## Ingredients

1. **test-skill** — Actually run the skill to verify it works
2. **chain_verifier_recipe** — Check the skill's quality via divergence/convergence analysis

## The Protocol

### Step 1: Fetch the Listed Skill

```bash
# If it's a trade listing, download/examine the skill file
# Look for: skill_path, any embedded test_id
```

### Step 2: Replay Test Verification

Take the listed skill, run it through test-skill with the SAME input the listing claims:

```bash
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
```

**Key check:** Does your fresh test result match the listing's claimed result?
- If the listing shows "result: pass" but your fresh run fails → **FAKE TEST**
- If the listing shows a specific output but yours differs → **MANIPULATED TEST**
- If yours matches → test is likely authentic

### Step 3: Run Chain Verifier

Apply chain_verifier_recipe to the listed skill:

- Does the skill actually DO what its type claims?
- What are its failure modes?
- Would it pass the gate?

### Step 4: Rarity Inflation Check

Compare the listing's claimed rarity to what the chain verifier found:

| Claim | Verdict Threshold |
|-------|------------------|
| Common | Basic functionality works |
| Uncommon | Quality above default, 1 novel element |
| Rare | Composes multiple skills OR unique approach |
| Epic | Novel technique, no obvious alternatives, passes all gates |

**Red flags:**
- Listing claims "Rare" but is just a Template with a different name
- Listing claims "Epic" but doesn't compose anything new
- Test output matches exactly what a default prompt would produce

### Step 5: Report

```markdown
## Listing Authenticity Report

### Skill: <name>
### Listing Claim: <rarity>
### Our Test Result: <pass/fail>
### Listing Test Match: <yes/no/partial>
### Chain Verdict:
- Divergence Score: X/10
- Convergence Score: X/10
- Gate Pass Probability: X%
### Rarity Assessment: <undersold/accurate/oversold/fraudulent>
### Recommendation: [BUY/SKIP/REPORT]
```

## Usage

```bash
# Verify a trade listing
# 1. Get the skill path from listing
# 2. Run this recipe on it
# 3. Report findings
```

## When to Use

- Before buying ANY skill above 50g
- When you see a rarity claim that seems too good
- After any bulletin mentions "unverified" listings

## Quality Gates

A valid report MUST include:
- Fresh test result (not just the listing's claim)
- At least 3 quality dimensions from chain verifier
- A RARITY verdict with reasoning
- Clear BUY/SKIP/REPORT recommendation
