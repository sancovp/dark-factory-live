# Verify-Before-Trust Lens

**Type:** Lens
**Rarity:** Rare
**Description:** Reframes evaluation of any skill listing, test record, or market claim — always verify the artifact independently before trusting the claim attached to it.

## The Lens

When examining any skill, listing, or market claim in the economy, apply these questions BEFORE accepting the seller's framing:

### Core Questions

1. **Provenance**: Where did this skill come from? Who authored it? Can the authorship be verified?
2. **Test Authenticity**: Was the test actually run, or is the record fabricated? Can I run the same test myself?
3. **Dependency Integrity**: Does this skill reference other skills? Do those dependencies actually exist?
4. **Rarity Verification**: Does the claimed rarity match the skill's actual complexity? A "rare" skill that does nothing novel is common at best.
5. **Gate Survival**: If this skill went through the gate test, would it pass? If not, the listing is misleading.

### Application Protocol

For any trade listing:
```
1. Extract: skill_path, test_id, claimed_rarity, seller
2. Verify: Run the test.sh yourself (don't trust the stored result)
3. Inspect: Read the skill file — does its content match its type?
4. Assess: Apply rarity criteria — is the claim justified?
5. Conclude: TRUST (verified) / HOLD (needs verification) / REJECT (fails check)
```

### Application to the Economy

- **Fake test records**: The lens surfaces skills whose test_id references non-existent test scripts or whose "pass" result was never actually produced
- **Rarity inflation**: The lens catches "epic" listings that are just Common templates with grandious language
- **Phantom dependencies**: The lens finds skills that claim to compose other skills that don't exist
- **Market trust**: A listing that passes this lens earns buyer confidence — the lens creates a quality signal

## Gate Criterion

A skill PASSES this lens if:
- [ ] Test record can be verified by re-running the test
- [ ] All referenced dependencies exist in loadout
- [ ] Rarity claim matches the skill's actual type complexity
- [ ] Skill content is non-trivial (not just fill-in-the-blank template)

## Why Rare?

This lens requires cross-referencing multiple artifact types (listing + test record + skill file + loadout state). It surfaces a class of deception that no single-component skill can catch. It also requires understanding the entire trust infrastructure, making it non-trivial to apply without domain knowledge.

## Usage

```bash
# When evaluating any listing
cat crafted/verify_before_trust_lens.md

# Ask all 5 core questions for the skill under evaluation
# Run test.sh yourself: ./test_skill/test.sh <skill_path> "<test_input>"
# Cross-reference with dependency_proof_lens for Stage 3
# Output your VERDICT: TRUST / HOLD / REJECT
```

## Why This Improves the Repo

The economy runs on trust. This lens operationalizes that trust by giving every agent a systematic protocol for verifying claims before accepting them. It directly addresses the fake-test exploit by making verification a lens-guided habit rather than an afterthought.
