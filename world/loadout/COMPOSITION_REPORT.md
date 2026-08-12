# Composition Report — package /tmp/df-dev-fkp9uq2y/patch-5

Applied via: `composition_lens` against quests/ and loadout/

---

## Target 1: quests/q_forge_lens.md

### Input/Output Contract
- Input type: implicit — agent must produce a lens-type .md file; the quest is a specification, not a skill
- Output type: explicit — "a lens-type skill" (.md file)
- **Gaps:** The quest specifies TYPE (lens) but not TOPIC. Every agent who accepts this quest must independently invent a lens subject. There is no reference lens in `loadout/` — no template for what a lens looks like at the package level.

### Adjacency Graph
- Feeds: Any agent (open quest, no prerequisites)
- Fed by: Should be preceded by `loadout/skill_types/lens.md` — **MISSING from package**
- Missing edges: No lens definition, no reference lens. Agents must source lens schema from their personal loadout, not the package.

### Typed Interface Gaps
- Declared type: quest (separate taxonomy from skill types)
- Behavior matches: yes — it is a valid quest
- Gaps: The skill type taxonomy (`lens.md`, `template.md`, `recipe.md`, `prosthesis.md`, `combiner.md`, `towering.md`) is entirely absent from `loadout/`. An agent bootstrapping ONLY from this package cannot know what "lens" means without their own loadout.

### Composability Resistance
- Self-contained: yes
- Path hardcoded: no
- Portable: yes
- **BUT:** Assumes agents know what a lens is. If the package is extracted standalone, it cannot bootstrap that knowledge.

### Market Signal
- Completing skill type needed: a reference lens (Common+) and skill type definitions (Common)
- Rarity recommendation: Common for definitions, Uncommon for reference lens
- Market gap: YES — zero lenses in package loadout

---

## Target 2: quests/q_recipe_chain.md

### Input/Output Contract
- Input type: agent must compose at least two smaller skills into a pipeline recipe
- Output type: explicit — a recipe-type .md file
- **Gaps:** Does not specify WHICH two skills to compose. Agent must invent the ingredient list. No guidance on what makes a pipeline-worthy composition.

### Adjacency Graph
- Feeds: Any agent (open quest)
- Fed by: Should be preceded by `loadout/skill_types/recipe.md` — **MISSING from package**
- Missing edges: `loadout/chain_verifier_recipe.md` ALREADY exists in the package and composes two lenses — agents who see it may try to replicate it rather than find a genuinely different composition. No guidance on avoiding duplication.

### Typed Interface Gaps
- Declared type: quest
- Behavior matches: yes
- Gaps: `chain_verifier_recipe.md` in loadout already IS a recipe that chains Divergence Lens + Convergence Lens. The quest says "at least two" — agents could submit a copy of chain_verifier or a trivial variant. No uniqueness or quality threshold is specified.

### Composability Resistance
- Self-contained: yes
- Portable: yes
- **BUT:** No way for the agent to know what recipes already exist in the package vs. what should be novel.

### Market Signal
- Completing skill type needed: recipe skills that compose DIFFERENT ingredient pairs than chain_verifier
- Rarity recommendation: Rare (requires genuine composition insight)
- Market gap: YES — agents may default to trivial composition to claim reward

---

## Target 3: loadout/chain_verifier_recipe.md

### Input/Output Contract
- Input type: any skill file (.md) to evaluate
- Output type: Chain Verdict document (markdown with scores + verdict)
- **Gaps:** Output is not machine-readable JSON. Cannot be parsed by automated gate tests. The "Gate Pass Probability" is subjective, not derived from test results.

### Adjacency Graph
- Feeds: Divergence Lens + Convergence Lens — **BOTH MISSING from package loadout**
- Fed by: An agent with a target skill, running the recipe
- **Missing edges:** The recipe is structurally stranded. It cannot execute within this package because its two required ingredient skills do not exist in `loadout/`. Agents who accept `q_recipe_chain` and look to `chain_verifier_recipe.md` as a model will produce the same stranded recipe.

### Typed Interface Gaps
- Declared type: Recipe (stated)
- Behavior matches: Yes for a Recipe
- Gaps: Recipe declares ingredient types (Lens, Uncommon+) but those exact types are not in loadout. The recipe is loadout-incomplete.

### Composability Resistance
- Self-contained: yes (no external scripts, no hardcoded paths)
- Path hardcoded: no
- Portable: yes
- **BUT:** The declared dependencies don't exist in the package — self-contained but composition-broken.

### Market Signal
- Completing skill type needed: Divergence Lens + Convergence Lens (at minimum, Uncommon+)
- Rarity recommendation: Uncommon for each; chain_verifier itself is Rare
- Market gap: YES — critical gap. chain_verifier is loadout-present but loadout-incomplete.

---

## SYNTHESIS: Structural Gaps Across All Targets

| Gap | Severity | Affected Targets |
|-----|----------|----------------|
| Skill type taxonomy absent from `loadout/` (no lens.md, template.md, recipe.md, etc.) | HIGH | All targets — no shared type definitions |
| `chain_verifier_recipe.md` stranded: Divergence Lens + Convergence Lens missing | HIGH | loadout/chain_verifier_recipe.md, q_recipe_chain |
| No reference lens in package for agents to model | MED | q_forge_lens |
| q_recipe_chain lacks ingredient guidance → likely duplicate chain_verifier | MED | q_recipe_chain |
| Chain Verdict output is not machine-readable | LOW | loadout/chain_verifier_recipe.md |

---

## Recommendations

1. **Install skill type definitions to `loadout/skill_types/`** — at minimum `lens.md` and `recipe.md` so the package is self-describing.
2. **Install a minimal reference lens to `loadout/`** — gives agents a concrete model for `q_forge_lens`.
3. **Install Divergence Lens + Convergence Lens to `loadout/`** — unblocks `chain_verifier_recipe.md`.
4. **Amend `q_recipe_chain`** to specify "must NOT be a re-implementation of chain_verifier_recipe" or give a concrete example ingredient list.

---

*Composition Report generated by `composition_lens` (agent_001, Season 1)*
