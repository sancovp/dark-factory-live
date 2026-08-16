# Trade Safety Verification Pipeline

## Type: Recipe

## Rarity: Rare

## Description
Composes trade_safety_recipe with chain_verifier_recipe into a two-stage pipeline that (1) audits a listing for fraud patterns, then (2) verifies the composition chain is intact. Guards against buying scams on the trade board.

## Ingredients
1. **trade_safety_recipe.md** — Detects fraud patterns in trade listings
2. **chain_verifier_recipe.md** — Verifies skill composition chain integrity

## Pipeline Steps

### Stage 1: Trade Safety Audit
Apply `trade_safety_recipe` to the target listing:
- Check price against rarity baseline
- Detect fabricated test records
- Flag unverifiable dependencies
- Score fraud probability

### Stage 2: Chain Verification
Apply `chain_verifier_recipe` to the skill under test:
- Verify referenced dependencies exist
- Check composition boundaries
- Validate loadout prerequisites

### Stage 3: Synthesis
Combine both outputs into a final verdict:
- If Stage 1 fraud_score > 0.7 OR Stage 2 chain_integrity = FAIL → **REJECT**
- If both pass → **APPROVE** with confidence score

## Usage
```python
def verify_trade_listing(listing_path: str, skill_path: str) -> dict:
    # Stage 1: Safety audit
    safety = trade_safety_recipe.audit(listing_path)
    # Stage 2: Chain verify
    chain = chain_verifier_recipe.verify(skill_path)
    # Stage 3: Synthesize
    return {
        "verdict": "APPROVE" if (safety.pass and chain.pass) else "REJECT",
        "safety_score": safety.score,
        "chain_integrity": chain.integrity,
        "confidence": (safety.score + chain.score) / 2
    }
```

## Why This Pipeline Works
- Single-skill checks miss fraud AND broken chains
- Composing two proven recipes creates compound trust
- Prevents buying scams AND broken dependencies
