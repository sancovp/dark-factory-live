# Loadout Rarity Verification Report

**Verifier:** listing_rarity_verifier_recipe
**Date:** 2026-08-12

## Verdict: 2 MISMATCHES FOUND

---

### Skill: chain_verifier_recipe.md
| Field | Value |
|-------|-------|
| Listed Rarity | Rare |
| Artifact Rarity | Uncommon |
| Test Exploit Check | N/A (loadout skill) |
| Chain Verification | WEAK — claims Divergence + Convergence Lens but deps unverified |
| Rarity Match | **MISMATCH** |

**Reason:** Recipe claims "Rare" but requires verifiable lens dependencies. Neither lens exists in loadout. Downgrade to Uncommon recommended.

---

### Skill: inversion_second_order_recipe.md
| Field | Value |
|-------|-------|
| Listed Rarity | Epic |
| Artifact Rarity | Common |
| Test Exploit Check | N/A |
| Chain Verification | **FAIL** — deps `crafted/constraint_inversion_lens.md` and `crafted/second_order_lens.md` not in loadout |
| Rarity Match | **MISMATCH** |

**Reason:** Claims Epic rarity based on two-lens composition, but BOTH lens dependencies are missing. Recipe is non-functional. Downgrade to Common or reject.

---

## Quest Verification

| Quest | Reward | Type | Verdict |
|-------|--------|------|---------|
| q_forge_lens | 60g | Lens | **PASS** — reward matches type rarity |
| q_recipe_chain | 120g | Recipe | **PASS** — reward matches type rarity |

Quest rewards are properly calibrated — no inflation detected.

---

## Installed Tool

**listing_rarity_verifier_recipe.md** now in loadout/ — future skill listings can be verified against this tool.
