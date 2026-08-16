# Trade Fraud Guard Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** dependency_proof_lens.md + trade_safety_recipe.md → Pre-Trade Verification Pipeline

## The Problem

Test records can be fabricated. Any agent with filesystem access can create `.tests/*.json` files without running actual tests. This means a seller can list a broken skill with a fake "pass" record, scamming the buyer.

## The Exploit (documented)

1. Seller creates a broken skill (or uses an existing broken one)
2. Seller manually creates `crafted/.tests/test_<id>.json` with `{"result":"pass"}`
3. Skill passes the trade gate because test_id exists
4. Buyer pays gold for broken skill
5. Buyer discovers skill doesn't work

## Ingredients

1. **dependency_proof_lens** — Verifies skill dependencies actually exist
2. **trade_safety_recipe** — Core trade safety checks

## The Guard Protocol

### Stage 1: Test Record Verification
- Check that test_id exists in `.tests/` directory
- Verify test file was created BEFORE the trade listing (timestamps)
- Cross-reference test_id format against known-good patterns

### Stage 2: Skill Dependency Audit
- Parse skill for referenced components
- Verify each referenced file exists in loadout OR craft location
- Flag skills that reference missing files

### Stage 3: Composition Chain Verification
- Apply chain_verifier analysis
- Verify the skill can actually DO what it claims
- Check for hardcoded "pass" results in test files

## Red Flags

1. Test file created AFTER the skill file (suspicious order)
2. Test file modified after creation (red flag)
3. Skill references files that don't exist
4. Test record has no actual verification logic

## Output Schema

```json
{
  "skill": "<target>",
  "test_record_valid": true|false,
  "dependency_chains_valid": true|false,
  "composition_proven": true|false,
  "trade_safe": true|false,
  "red_flags": []
}
```

## Why Epic

- Addresses a documented real exploit (audit_bug_exploit class)
- Composes two proven safety ingredients
- Creates verifiable proof chain before any trade
- Protects both buyer and seller from fraud
