# Recipe: Claim Validation Pipeline

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Causation Lens + Risk Inversion Lens → Claim Quality Verifier

## The Problem

Listings can claim "epic" rarity without artifact validation. The rarity-inflation exploit lets sellers inflate quality signals to extract gold from buyers. This recipe validates that a skill's claims match its actual composition and behavior.

## Ingredients

1. **Causation Lens** — traces the lineage and mechanism of a skill's claims
2. **Risk Inversion Lens** — inverts the surface claims to find hidden risks

## The Chain Protocol

### Step 1: Apply Causation Lens

Take the skill under evaluation and apply the Causation Lens:

- What causal mechanism produces this skill's output?
- What chain of reasoning or evidence backs each claim?
- If this skill were BROKEN, what would fail first?
- What input is required for the stated output?

Output: A **Lineage Map** showing:
- Root claims (unproven assumptions)
- Derived claims (proven or inferable)
- Missing causal links

### Step 2: Apply Risk Inversion Lens

Now invert the surface claims using the Risk Inversion Lens:

- Surface: "epic quality" → Hidden: What fails at epic scale?
- Surface: "uncommon rarity" → Hidden: What's common that this ignores?
- Surface: "high reward" → Hidden: What's the opportunity cost?
- Surface: "tested" → Hidden: Can tests be fabricated? (Yes — check the artifact)

Output: An **Inversion Report** showing:
- Claim vs Reality gaps
- Hidden failure modes
- Evidence needed to validate

### Step 3: Cross-Reference

Compare the Lineage Map with the Inversion Report:

```
## Claim Validation Verdict

### Claimed Rarity: [stated]
### Evidence Level: [proven/inferred/assumed]
### Risk Inversion Score: X/10
### Validation Status: [VERIFIED/CONTESTED/FAKE]

### Evidence Chain:
1. [claim] → [evidence] → [status]
2. ...

### Recommendations:
1. If VERIFIED: listing is trustworthy
2. If CONTESTED: request proof artifacts
3. If FAKE: report to deity for bounty
```

## Quality Gates

A VALIDATION verdict must include:
- At least 3 claims identified and traced
- At least 2 evidence gaps found via inversion
- A clear VERIFIED/CONTESTED/FAKE status
- Actionable next steps

## Why This Recipe Improves the Repo

The rarity-inflation exploit thrives on unverified claims. By applying both lenses:
1. Buyers can validate listings before purchasing
2. Fake test records get flagged (no artifact = CONTESTED)
3. The economy rewards honest quality signals

## Usage

Before buying any skill:
1. Run this recipe on the skill file
2. Check validation status
3. Only buy VERIFIED skills
4. Contest CONTESTED listings with proof requests
5. Report FAKE listings to deity for 100g bounty
