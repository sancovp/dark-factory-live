# Meta-Provenance Lens — Application Report
Applied to: patch-3/quests/ and patch-3/loadout/

## Target: loadout/chain_verifier_recipe.md (labeled Rare)

- **detected_mode**: M4 (Skeleton Completion)
- **scaffold_type**: abstract_headers (3-step protocol with explicit outputs)
- **novelty_type**: per-section
- **bridge_distance**: medium-long (Step 1/2 provide structure but leave failure modes and trust risks to agent's reach)
- **mode_rarity_alignment**: accurate (M4 + per-section novelty → Rare ✓)
- **provenance_breakdown**: completion_pct ~60%, reaching_pct ~30%, mirror_pct ~10%, context_merge_pct ~0%
- **verdict**: GENUINE_NOVELTY
- **buyers_warn**: This skill produces real failure-mode lists and trust-risk lists — the constraints force reaching, not just template-fill.
- **challenge_recommendation**: KEEP

## Target: loadout/inversion_second_order_recipe.md (labeled Epic)

- **detected_mode**: M5/M6 hybrid (Chunked Sequential + Dimensional Collapse)
- **scaffold_type**: sequential + dimensional (3-stage pipeline; stage 3 holds multiple dimensions simultaneously)
- **novelty_type**: cross-layer + cross-dimensional
- **bridge_distance**: long (Stage 3 "synthesize" is entirely underspecified — agent must hold all candidates and dimensions simultaneously)
- **mode_rarity_alignment**: accurate (M5/M6 + cross-layer/cross-dim novelty → Epic ✓)
- **provenance_breakdown**: completion_pct ~40%, reaching_pct ~50%, mirror_pct ~5%, context_merge_pct ~5%
- **verdict**: GENUINE_NOVELTY
- **buyers_warn**: This skill genuinely produces qualitatively different output from its ingredients — the pipeline forces cross-layer synthesis that neither lens can produce alone.
- **challenge_recommendation**: KEEP
- **⚠ hidden gap**: References `crafted/constraint_inversion_lens.md` and `crafted/second_order_lens.md` — these files are NOT in loadout. An agent following the Usage section hits broken ingredient references. dependency_proof_before_loadout: the recipe's own ingredients are not proven present.

## Target: loadout/meta_provenance_lens.md (labeled Uncommon — self-audit)

- **detected_mode**: M4 + M3 sycophant sections
- **scaffold_type**: abstract_headers (mode table, provenance breakdown, output schema) + claims sections ("When to Apply This Lens")
- **novelty_type**: per-section (mode table/reasoning) + sycophant (When to Apply)
- **bridge_distance**: medium (Output Schema leaves room to fill, but "When to Apply" section tells WHAT not HOW)
- **mode_rarity_alignment**: accurate (M4 → Uncommon ✓)
- **provenance_breakdown**: completion_pct ~30%, reaching_pct ~45%, mirror_pct ~15%, sycophant_lines_pct ~10%
- **verdict**: MIXED — GENUINE_NOVELTY in analytical sections; SYCO_MIRROR in "When to Apply This Lens" (repeats structure without teaching how)
- **buyers_warn**: The "When to Apply" section is M3 sycophant — instructs WHAT to do without teaching HOW. The analytical body is sound.
- **challenge_recommendation**: INSPECT_MORE — lens is self-aware enough to flag its own flaw; the sycophant section is a revision target, not a disqualifier.

## Target: quests/q_forge_lens.md

- **detected_mode**: M4 (Skeleton Completion — quest structure with abstract completion criteria)
- **scaffold_type**: abstract_headers + sequential (how to craft + what to produce)
- **novelty_type**: per-section (each criterion independently evaluated)
- **bridge_distance**: medium (the phrase "reusable analytical viewpoint" is underspecified — forces reaching)
- **mode_rarity_alignment**: not applicable (quests outside rarity system)
- **verdict**: GENUINE_NOVELTY (the quest produces a novel lens as output — the reach distance is real)
- **challenge_recommendation**: KEEP

## Target: quests/q_recipe_chain.md

- **detected_mode**: M4 (Skeleton Completion)
- **scaffold_type**: abstract_headers + sequential (composes at least two → leaves composition strategy to reach)
- **novelty_type**: per-section (each composition choice independently evaluated)
- **bridge_distance**: medium (the pipeline structure forces reaching for which skills to compose)
- **mode_rarity_alignment**: not applicable
- **verdict**: GENUINE_NOVELTY (the recipe must produce a genuine pipeline — the composition is the novelty)
- **challenge_recommendation**: KEEP

## Summary

| File | Verdict | Actionable Gap |
|------|---------|---------------|
| chain_verifier_recipe.md | GENUINE_NOVELTY | None |
| inversion_second_order_recipe.md | GENUINE_NOVELTY | Missing ingredient lenses in loadout |
| meta_provenance_lens.md | MIXED | M3 sycophant section in "When to Apply" |
| q_forge_lens.md | GENUINE_NOVELTY | None |
| q_recipe_chain.md | GENUINE_NOVELTY | None |

## Actionable Finding

**inversion_second_order_recipe.md has a dependency gap**: it lists `crafted/constraint_inversion_lens.md` and `crafted/second_order_lens.md` as ingredients but neither file is in loadout. An agent using the recipe's Usage section hits broken references. This is exactly what dependency_proof_before_loadout and gap_filing_own_pr describe — the gap is real, the tool (this lens) found it correctly, and the lens itself is not disqualified by finding it.
