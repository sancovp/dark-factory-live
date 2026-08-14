# Meta Rarity Honesty Pipeline — Verification Report

## Pipeline Run Against loadout/

### Stage 1: Convergence Detection

**Input:** `chain_verifier_recipe.md` vs `inversion_second_order_recipe.md`

**Structural Comparison:**
| Pattern | chain_verifier | inversion_second_order |
|---------|---------------|----------------------|
| Header format | Type/Rarity/Composes | Type/Rarity/Composes |
| Stage structure | 3-step pipeline | 3-stage pipeline |
| Quality Gate | ## Quality Gates (checkbox) | ## Quality Gate (checkbox) |
| Ingredient format | Numbered list | Numbered list |
| Composition claims | "catches MORE" | "non-obvious composition" |

**Convergence Detection Result:**
```json
{
  "skills_flagged": ["chain_verifier_recipe.md", "inversion_second_order_recipe.md"],
  "convergence_type": "uncommon",
  "pattern_description": "Both recipes follow identical Recipe type scaffolding with 3-stage pipelines"
}
```

### Stage 2: Meta-Eval for Honest Rarity

**chain_verifier_recipe.md:**
| Mechanism | Finding |
|-----------|---------|
| Provenance | Mostly MIRROR (standard lens-composition patterns) + ATTRACTOR (common pipeline advice) |
| Bridge Distance | Right (provides scaffolding but requires reader application) |
| Surface-Process | Weak (claims "catches MORE failures" but no structural proof) |
| **Honest Rarity** | **Uncommon** (downgrade from claimed Rare) |

**inversion_second_order_recipe.md:**
| Mechanism | Finding |
|-----------|---------|
| Provenance | Mixed COMPLETION + NOVELTY (constraint inversion + second-order is genuinely novel) |
| Bridge Distance | Right (structured but requires application) |
| Surface-Process | Strong (stages explicitly named, scored, ordered) |
| **Honest Rarity** | **Epic** (matches claimed Epic) |

### Stage 3: Trust Verdict Synthesis

```json
{
  "loadout_skills": [
    {
      "listing_id": "chain_verifier_recipe.md",
      "claimed_rarity": "Rare",
      "honest_rarity": "Uncommon",
      "convergence_type": "uncommon",
      "trust_verdict": "CAUTION",
      "savings_vs_claimed": "If bought at Rare price (60g), overpaying by ~40g",
      "recommendation": "Downgrade expectations or negotiate price"
    },
    {
      "listing_id": "inversion_second_order_recipe.md",
      "claimed_rarity": "Epic",
      "honest_rarity": "Epic",
      "convergence_type": "legitimate_rare",
      "trust_verdict": "TRUST",
      "savings_vs_claimed": "0g (fair price)",
      "recommendation": "Buy at listed Epic price"
    }
  ]
}
```

### Quality Gate Checklist

- [x] Stage 1 identified 2 convergent skills (chain_verifier + inversion_second_order share same Recipe structure)
- [x] Stage 2 produced honest_rarity for each (Uncommon vs Epic)
- [x] Stage 3 output specific TRUST/CAUTION verdicts
- [x] Savings vs claimed calculated (40g potential overpay for chain_verifier)

### Pipeline Installed

Installed to `loadout/`:
- `meta_eval_lens.md`
- `convergence_detector_lens.md`
- `meta_rarity_honesty_recipe.md`

All skills ready for agent use on boot.
