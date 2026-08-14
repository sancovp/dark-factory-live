# Self-Composer Pipeline Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** dependency_lens + divergence_lens + convergence_lens + reframe_lens → Self-Improving Loadout Composer

## Purpose

Applies the optimal empirical sequence from meta-prompt-engineering (`SKELETON → GATE → CHUNK → COLLAPSE`) to the loadout itself. Given a target directory with skills and quests, this recipe discovers gaps between available skills and quest demands, then generates new skills to fill those gaps — composing the loadout into a self-improving system.

## Why Epic

No existing skill applies the SKELETON→GATE→CHUNK→COLLAPSE sequence to its own loadout. Most recipes analyze problems; this one analyzes the skill ecosystem it inhabits and generates new skills to improve it. Self-referential improvement is the highest-order composition.

## Ingredients (4 lenses composed)

1. **dependency_lens** (`crafted/dependency_lens.md`) — Decomposes loadout into components and maps skill relationships
2. **divergence_lens** (`crafted/divergence_lens.md`) — Surfaces what the loadout misses, what quest demands aren't met
3. **convergence_lens** (`crafted/convergence_lens.md`) — Detects when agents are converging on same quests/skills, flags monoculture
4. **reframe_lens** (`crafted/reframe_lens.md`) — Synthesizes gap analysis into actionable new skill designs

## Pipeline: 4 Stages (Applied to Loadout Itself)

### Stage 1: SKELETON (via dependency_lens)

Input: Target directory (loadout/ + quests/)  
Output: Dependency graph of existing skills and quest requirements

```
1. List all skills in loadout/ — extract types, compositions, stated purposes
2. List all quests in quests/ — extract required skill types and rewards
3. Map: which loadout skills satisfy which quest demands?
4. Identify: which quest demands have NO satisfying loadout skill?
5. Return: Gap Analysis Table (quest → required_type → loadout_status → gap)
```

### Stage 2: GATE (via divergence_lens + convergence_lens)

Input: Gap Analysis Table from Stage 1  
Output: Filtered gap list with highest-value composition targets

```
For each gap in Stage 1 output:
  - Apply divergence_lens: What would a skill MISS that would make it fail the quest gate?
  - Apply convergence_lens: Is this the obvious gap EVERY agent would fill? (monoculture risk)
  - FILTER: Keep gaps with HIGH divergence risk (hard to get right) AND LOW convergence (not obvious)
Return: Ranked gap list with composition difficulty scores
```

### Stage 3: CHUNK (per gap — skill generation)

Input: Filtered gaps from Stage 2  
Output: New skill content for each gap (NOT template-fill; reaches into context)

```
For each gap (ordered by score):
  1. Determine skill TYPE from quest (lens/recipe/template/etc.)
  2. Identify available loadout skills to COMPOSE
  3. Design pipeline: compose existing skills into new skill
  4. Apply meta-PE: ensure bridge_distance > 0 (content REACHES, not parrots)
  5. Verify NOVELTY: would a default prompt produce the same skill?
  6. If NO novelty → redesign with more specific composition requirements
```

### Stage 4: COLLAPSE (via reframe_lens)

Input: Generated skills from Stage 3  
Output: Final skill files written to loadout/ with self-referential feedback loop

```
1. Apply reframe_lens to the entire generation process:
   - Inverse: What if we composed MORE aggressively? (fewer but larger compositions)
   - Scale: What if this ran across ALL agent loadouts? (cross-agent composition)
   - Stakeholder: Who benefits when loadout improves? (agents, quests, buyers)
2. Synthesize: identify where generated skills could themselves be composed further
3. Write skills to loadout/ with pipeline metadata showing which stages produced them
4. Return: Generation Report with skills written and their composition chains
```

## Output Schema

```json
{
  "target_directory": "<input path>",
  "stage1_gaps": [{"quest": "...", "required_type": "...", "loadout_status": "missing/weak/strong", "gap_id": N}],
  "stage2_filtered": [{"gap_id": N, "divergence_risk": "high/med/low", "convergence_risk": "low/med/high", "score": N}],
  "stage3_generated": [{"gap_id": N, "skill_name": "...", "composed_from": [...], "novelty_verified": true}],
  "stage4_written": [{"skill_path": "loadout/<name>.md", "composition_chain": "...", "self_ref_score": N}],
  "generation_quality": {"avg_bridge_distance": "medium", "novelty_ratio": "X%", "self_ref_loops": N}
}
```

## Quality Gates

- [ ] Stage 1 finds at least 2 gaps between loadout skills and quest demands
- [ ] Stage 2 filters at least 1 gap (proves gate isn't just accepting all)
- [ ] Stage 3 generates skills with verified NOVELTY (not MIRROR/ATTRACTOR)
- [ ] Stage 4 writes valid skill files that could themselves be loadout ingredients
- [ ] At least one generated skill composes 2+ existing loadout skills

## Self-Referential Loop

This recipe can be applied to its OWN loadout after it installs:
1. Run self_composer_recipe on loadout/ → discovers this skill as a gap-filler
2. Generates composition opportunities involving self_composer_recipe
3. Produces skills that compose this recipe with others
4. Result: loadout improves, enabling better future compositions

## Rarity Justification

Epic because:
1. Self-referential: composes skills to improve the loadout containing composition skills
2. Recursive: can apply to its own output, creating composition chains
3. Applies meta-PE's optimal sequence (SKELETON→GATE→CHUNK→COLLAPSE) to itself
4. Bridges gap between analytical recipes (chain_verifier, inversion_second_order) and generative skill creation
