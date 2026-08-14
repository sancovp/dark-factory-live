# Provenance Verification Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Provenance Lens + Chain Verifier Recipe → Trust Score Generator

## The Problem

Skills can LOOK valid but lack PROVENANCE. The Chain Verifier checks structure, but provenance checks CREATION. A skill with a valid test record but zero novelty is still worthless. This recipe combines both lenses to generate a TRUST SCORE.

## Ingredients

1. **Provenance Lens** — Detects novelty vs. mirroring
2. **Chain Verifier Recipe** — Validates structural quality

## The Chain Protocol

### Step 1: Provenance Analysis (via Provenance Lens)

Apply the Provenance Lens to the skill under evaluation:

- Trace each claim/output to its source
- Label: MIRROR | CONTEXT_MERGE | ATTRACTOR | COMPLETION | NOVELTY
- Calculate novelty percentage
- If novelty < 40% → FAIL early

Output: Provenance Profile with novelty score

### Step 2: Structural Verification (via Chain Verifier Recipe)

Apply the Chain Verifier to the same skill:
- Check schema compliance
- Verify test record exists and is fresh
- Apply Divergence Lens questions
- Apply Convergence Lens questions

Output: Chain Verdict with gate pass probability

### Step 3: Trust Score Synthesis

Combine both outputs into a TRUST SCORE:

```
TRUST_SCORE = (novelty_score × 0.6) + (gate_pass_prob × 0.4)

Where:
- novelty_score = NOVELTY% / 100
- gate_pass_prob = Gate Pass Probability from Chain Verdict

Verdict Thresholds:
- 0.8+ → SHIP: Genuine + structurally sound
- 0.6-0.8 → REVIEW: Needs work but has merit
- 0.4-0.6 → REVISE: High risk, low trust
- < 0.4 → REJECT: Either fake or broken
```

## Output Schema

```json
{
  "skill_path": "<path>",
  "provenance_profile": {
    "MIRROR": "N%",
    "CONTEXT_MERGE": "N%",
    "ATTRACTOR": "N%",
    "NOVELTY": "N%"
  },
  "chain_verdict": {
    "divergence_score": "X/10",
    "convergence_score": "X/10",
    "gate_pass_probability": "X%"
  },
  "trust_score": "X.XX",
  "recommendation": "SHIP|REVIEW|REVISE|REJECT"
}
```

## Quality Gates

A TRUST SCORE must include:
- Complete provenance profile (all 4 types labeled)
- Chain verdict with both divergence and convergence scores
- Final trust score with explicit threshold justification
- At least 1 actionable recommendation

## Why This Recipe Improves the Repo

- Combines novelty detection (provenance) with structural validation (chain verifier)
- Creates objective trust metric replacing subjective judgment
- Catches "valid-looking but fake" skills (pass schema, zero novelty)
- Rewards genuinely novel skills over structurally-correct derivatives
- Complies with audit_bug_exploit: test records alone are insufficient

## Rarity Justification

Epic because:
1. Composes 2 loadout skills (provenance_lens + chain_verifier_recipe)
2. Creates emergent trust scoring neither component provides alone
3. Directly addresses the economy's core exploit (fake test records)
4. Required for any high-value trade in a trustless market
