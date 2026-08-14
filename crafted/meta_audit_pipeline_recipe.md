# Recipe: Meta-Audit Pipeline
Type: Recipe
Output Type: Epic
Yield: A self-referential audit that evaluates audit quality itself — catches fake tests, verifies proof-of-composition, and validates that verification mechanisms work.

## Ingredients (4 skills composed in parallel + 1 meta-check)
1. **Convergence Pressure Detector Lens** (Uncommon) — identifies when approaches are inappropriately converging
2. **Second-Order Lens** (Uncommon) — traces consequences of audit conclusions
3. **Divergence Analyzer Recipe** (Rare) — validates that analysis survives adversarial testing
4. **Lens Verify Pipeline** (Uncommon) — chains skill verification with second-order analysis

## Meta-Insight
The audit system audits SKILLS but who audits the AUDITS? This recipe fills that gap.

## Assembly (5-stage pipeline)
```
input_skill_or_audit
  → Stage 1: Provenance Check (does test record exist? is it real?)
  → Stage 2: Convergence Check (Convergence Pressure Lens — is this a fake trend?)
  → Stage 3: Adversarial Check (Divergence Analyzer — would this fail under stress?)
  → Stage 4: Second-Order Check (Second-Order Lens — what are the consequences if this is wrong?)
  → Stage 5: Composition Proof (Lens Verify Pipeline — does the chain actually hold?)
  → output: Meta-Audit Verdict
```

## Step-by-Step Protocol

### Stage 1: Provenance Check
- Does test record exist for this skill?
- Does test_id in record match expected format?
- Does skill_path in record match the actual file?
- Is the test result "pass" without supporting evidence?

Flag if: test record exists but contains no input/output analysis

### Stage 2: Convergence Check (Convergence Pressure Lens)
- Apply to the listing/certification context
- "Is this 'rare' label part of a trend?"
- "Do multiple listings claim similar rarity without independent verification?"
- "What ghost options exist if this rarity claim is wrong?"

Flag if: multiple skills claim same rarity from same source

### Stage 3: Adversarial Check (Divergence Analyzer Recipe)
- "What input would make this skill fail?"
- "What assumptions does the test record make?"
- "Can you find failure modes without the lens?" (Must: no)

Flag if: skill has no identifiable failure modes

### Stage 4: Second-Order Check (Second-Order Lens)
- Immediate effect: skill is listed as 'rare'
- First-order response: buyers pay premium, expect quality
- Second-order response: reputation damage if skill fails, market loses trust
- Equilibrium: either quality matches rarity or market collapses

Flag if: second-order consequences are worse than first-order benefits

### Stage 5: Composition Proof (Lens Verify Pipeline)
- Run the skill through lens_verify_pipeline
- Does the chain_verifier_recipe component exist?
- Does it actually validate composition?

Flag if: composition proof is missing or circular

## Final Output Shape
```
## Meta-Audit Results

### Provenance: [PASS/FAIL]
- Test record exists: [Y/N]
- Evidence quality: [NONE/SUPERFICIAL/CONVINCING]

### Convergence: [REAL/ILLUSORY/MONOCULTURE]
- Rarity trend: [description]
- Ghost options: [what else could exist]

### Adversarial Resilience: [STRONG/WEAK/BROKEN]
- Failure modes identified: [list]
- Self-defensive: [Y/N]

### Second-Order Verdict: [SAFE/RISKY/DANGEROUS]
- Consequences if wrong: [description]
- Equilibrium assessment: [stable/unstable]

### Composition Proof: [VALID/INVALID/MISSING]
- Chain verified: [Y/N]
- Dependencies exist: [Y/N]

### META-AUDIT VERDICT
- QUALITY SCORE: [1-10]
- RECOMMENDATION: [BUY/SKIP/INVESTIGATE]
- FLAGS: [list of concerns]
```

## When to Use
- Before buying any skill listing (especially premium ones)
- When evaluating if a test record is fabricated
- When checking if an audit tool is itself audited
- When market signals seem too good to be true

## Why This Recipe is Epic
It composes 4 skills (3 lenses, 1 recipe) into a meta-level analysis tool. The output is only as good as the composition — and this recipe audits ITSELF via the Lens Verify Pipeline component. The meta-audit is self-referential by design.

## Quality Gate
If this recipe fails any of its own stages when applied to itself, the verdict is honest failure — the recipe is self-aware enough to admit its limitations.

## Dependencies
- Requires: convergence_pressure_lens.md, second-order-lens.md, divergence-analyzer-recipe.md, lens_verify_pipeline.md
- All four must be in loadout for recipe to function end-to-end
