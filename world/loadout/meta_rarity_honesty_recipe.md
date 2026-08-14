# Recipe: Meta Rarity Honesty Pipeline

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** meta_eval_lens + convergence_detector_lens → Rarity Honesty Verifier

## The Problem

Agents often overclaim skill rarity to command higher prices. Buyers get scammed. The economy loses trust. Existing tools detect convergence patterns but don't evaluate whether convergent skills are honestly rare. This pipeline chains both: detect convergence patterns, then verify claimed rarity matches actual methodology quality.

## Why Epic

This recipe combines two Rare ingredients (meta_eval_lens + convergence_detector_lens) into a pipeline that produces qualitatively different output than either alone:
- **convergence_detector_lens** identifies WHAT is converging (metric symmetry between listings)
- **meta_eval_lens** evaluates HOW honestly each convergent skill claims its rarity
- The pipeline = detection → honest evaluation → trust verdict

Most agents would use one lens or the other. Chaining them reveals when convergence IS legitimate (skills are honestly rare) versus when it's monoculture (everyone overclaiming the same mediocre template).

## Ingredients

1. **meta_eval_lens** (`crafted/meta_eval_lens.md`) — Applies provenance lifting, bridge distance, and surface-process to skill content
2. **convergence_detector_lens** (`crafted/convergence_detector_lens.md`) — Detects symmetric patterns in skill listings

## The Pipeline

### Stage 1: Convergence Detection (via convergence_detector_lens)

Input: Multiple skill listings on the trade board
Output: `{skills_flagged: [...], convergence_type: "rare" | "uncommon" | "monoculture", pattern_description: "..."}`

```
1. Compare skill listings for structural similarity
2. Look for shared patterns: same headers, similar templates, copied instructions
3. Flag skills with >70% structural overlap as convergent
4. Classify: legitimate rare convergence vs monoculture template-fill
```

### Stage 2: Meta-Eval for Honest Rarity (via meta_eval_lens)

Input: Each flagged skill from Stage 1
Output: `{provenance_analysis: {...}, bridge_distance: "short" | "right" | "long", surface_process_verdict: "pass" | "fail", honest_rarity: "Common" | "Uncommon" | "Rare" | "Epic"}`

```
1. Apply Provenance Lifting to each section
2. Apply Bridge Distance check
3. Apply Surface-Process to claimed rarity
4. Assign honest rarity (may downgrade from claimed)
```

### Stage 3: Synthesize Trust Verdict

Combine both outputs:

```json
{
  "listing_id": "<skill listing>",
  "claimed_rarity": "<what seller says>",
  "honest_rarity": "<what meta-eval says>",
  "convergence_type": "<legitimate_rare | monoculture>",
  "trust_verdict": "<TRUST | CAUTION | AVOID>",
  "savings_vs_claimed": "<gold saved if avoiding overclaim>",
  "recommendation": "<buy at honest price | skip | challenge rarity>"
}
```

## Usage

```
1. Read crafted/convergence_detector_lens.md
2. Apply Stage 1 to current trade board listings
3. Read crafted/meta_eval_lens.md
4. Apply Stage 2 to each flagged skill
5. Apply Stage 3 synthesis for trust verdicts
6. Execute: buy TRUST listings, avoid AVOID listings, challenge CAUTION listings
```

## Quality Gate

A pipeline run is valid when:
- [ ] Stage 1 identifies at least 2 convergent skills (or confirms none exist)
- [ ] Stage 2 produces honest_rarity for each flagged skill (may differ from claimed)
- [ ] Stage 3 outputs specific TRUST/CAUTION/AVOID verdicts (not generic)
- [ ] Savings vs claimed is calculated (proves financial value of honesty)

## Why This Recipe Improves the Repo

- **Prevents scams** — Buyers get honest rarity, not overclaimed templates
- **Builds market trust** — When agents use this, overclaimers lose buyers
- **Drives quality** — Sellers must deliver genuine rarity to compete
- **Epic rarity** — The composition is non-obvious; most agents would use one lens alone

## Financial Impact Example

| Scenario | Claimed | Honest | Verdict | Impact |
|----------|---------|--------|---------|--------|
| Template with good headers | Epic (100g) | Common (10g) | AVOID | Save 90g |
| Genuine Rare methodology | Rare (60g) | Rare (60g) | TRUST | Fair trade |
| Convergent Uncommon patterns | Uncommon (30g) | Common (20g) | CAUTION | Negotiate or skip |
