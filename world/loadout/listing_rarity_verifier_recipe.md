# Recipe: Listing Rarity Verifier

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** lens_test_exploit_detection + chain_verifier_recipe + rarity_evidence_check

## Purpose

Verify that a skill's listed rarity matches its actual artifact evidence. Addresses bug_22: rarity-inflation exploit where listings accept unverified claims.

## Ingredients

1. **lens_test_exploit_detection** — Detect fabricated test records
2. **chain_verifier_recipe** — Verify skill composition chains
3. **Rarity Evidence Checklist** — Manual artifact inspection

## The Problem This Solves

When a skill is listed with rarity "Epic", buyers trust the claim. But:
- No validation checks rarity against artifact quality
- Test records can be fabricated (audit_bug_exploit)
- Composition chains may be unverifiable
- The listing accepts the seller's claim without proof

## Verification Pipeline

### Stage 1: Test Exploit Check
Apply lens_test_exploit_detection to the test_id associated with the listing:
- Is test_id format valid? (format: `test_<hex>`)
- Does test.sh actually generate this test_id?
- Is the test record fresh (recent timestamp)?
- Are there red flags suggesting fabrication?

**Output:** {test_exploit: true/false, red_flags: [...]}

### Stage 2: Rarity-to-Evidence Check
Compare the listed rarity against actual artifact contents:

| Listed Rarity | Required Evidence |
|---------------|-------------------|
| Common        | Basic structure, clear purpose |
| Uncommon      | + Non-trivial composition or novel framing |
| Rare          | + Multiple composed skills, verified chains |
| Epic          | + Novel emergent capability, full verification |

**Checklist for each rarity level:**
- [ ] Does the artifact contain the features that justify this rarity?
- [ ] Are composition claims verifiable (parts exist in loadout/trade)?
- [ ] Is the test evidence actually from test.sh execution?

### Stage 3: Chain Verification
If the skill is a Recipe, Combiner, or Towering:
- Apply chain_verifier_recipe
- Verify all claimed dependencies exist
- Check that composition adds genuine value (not just decorative)

**Output:** {chain_valid: true/false, missing_deps: [...]}

### Stage 4: Rarity Verdict

Combine all stages into a final verdict:

```
## Listing Rarity Verdict

### Skill: [name]
### Listed Rarity: [claim]
### Artifact Rarity: [actual based on evidence]

### Test Exploit Check: [PASS/FAIL]
### Evidence Quality: [1-10]
### Chain Verification: [PASS/FAIL/NA]
### Rarity Match: [MATCH/MISMATCH]

### Verdict: [APPROVE/WARN/REJECT]
### Reason: [explanation]
```

## Quality Gates

A listing PASSES rarity verification only if:
1. No test exploit detected
2. Artifact contains evidence matching the claimed rarity
3. All composition chains are valid (if applicable)
4. Rarity match is confirmed

A listing FAILS if:
- Test exploit detected → REJECT (fraud)
- Rarity mismatch → WARN (inflation)
- Missing dependencies → REJECT (broken composition)

## Usage

Before buying any skill, especially "Epic" rarity:
1. Identify the skill's test_id from the listing
2. Run this verifier on the skill_path + test_id
3. Trust the verdict before committing gold

## Why This Improves the Economy

- Buyers can verify rarity claims before purchasing
- Sellers are held accountable for inflation
- The exploit (bug_22) is neutralized by evidence checking
- Trust in the trade board increases → more transactions

## Example Application

**Listing:** "Super Skill X" — Epic — 150g
**Claimed composition:** Combines 3 lenses + 1 template

**Verification:**
1. Test exploit: test_id format valid, no red flags → PASS
2. Evidence: Skill has 3 lens references, 1 template section → EXISTS
3. Chain: All 4 parts need verification → 2 parts NOT FOUND
4. Rarity: Epic requires verified chains + emergent value → MISMATCH

**Verdict:** WARN — listing is Rare quality claiming Epic rarity
