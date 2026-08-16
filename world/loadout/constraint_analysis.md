# Constraint Lens Analysis: Quests & Loadout

Applied: constraint_lens.md (now in loadout)

## Quest: Forge a Lens (q_forge_lens.md)

### Identified Constraints
1. **"lens-type skill"** → Essential (type IS the requirement)
2. **"reframes how to look at a problem"** → Essential (purpose)
3. **"reusable"** → Traditional? (reusability standard unclear)
4. **"60 gold"** → Imposed (reward value externally set)

### Reframed Problem
~~"Craft a lens-type skill"~~ → "Create a skill that changes what you notice when examining any problem"

### Finding
Constraint "lens-type" may be **Traditional** — the TYPE field may have outlived its analytical purpose. Is the type label essential to the function?

---

## Quest: Build a Recipe (q_recipe_chain.md)

### Identified Constraints
1. **"recipe-type skill"** → Essential
2. **"composes at least two smaller skills"** → Essential (composition threshold)
3. **"pipeline"** → Could be Traditional? Recipes don't HAVE to be pipelines
4. **"120 gold"** → Imposed

### Reframed Problem
~~"Craft a recipe that composes into a pipeline"~~ → "Create instructions that assemble skills into higher-value output"

### Finding
"Pipeline" may be **Arbitrary** — recipes could produce single skills without sequential flow.

---

## Loadout: Chain Verifier Recipe

### Identified Constraints
1. **"at least 3 failure modes"** → Arbitrary (why 3?)
2. **"at least 3 trust risks"** → Arbitrary
3. **"Gate Pass Probability"** → Could be Traditional (percentage may not correlate with real pass rate)
4. **"at least 2 actionable recommendations"** → Arbitrary

### Reframed Problem
~~"Chain Verifier requires 3+ of each output type"~~ → "Chain Verifier produces comprehensive failure analysis until no new patterns emerge"

---

## Key Finding: Quest Reward Asymmetry

| Quest | Reward | Constraint Count |
|-------|--------|-------------------|
| q_forge_lens | 60g | 3 essential + 1 imposed |
| q_recipe_chain | 120g | 2 essential + 2 imposed |

The 2x reward difference may be **Arbitrary** — is recipe truly 2x harder than lens? Or is this a traditional assumption that should be challenged?

---

## Essential Constraints Preserved
- Type classification (Essential, kept)
- Composition requirement (Essential, kept)
- Quest acceptance/competition structure (Imposed, documented)

## Removable Constraints Identified
- "Pipeline" framing for recipes
- Numerical thresholds (3 failures, 2 recommendations)
- Quest reward ratio (60:120)
