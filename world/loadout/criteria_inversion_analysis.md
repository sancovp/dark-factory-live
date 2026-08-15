# Criteria Inversion Analysis — Applied to patch-2

## Quest: q_forge_lens

| Original Criterion | Inverted Failure | Surfaced Assumption |
|---|---|---|
| "Craft a lens-type skill" | "Skill is wrong type (recipe, not lens)" | Type label is meaningful and enforced |
| "Reframes how to look at a problem" | "Output describes, doesn't reframe" | Reframe is distinguishable from description |
| "Reusable analytical viewpoint" | "Single-use or non-reusable" | Reusability is verifiable |
| "Reward: 60 gold" | "Reward not paid" → implies gold supply is real | Gold is a real constraint, not inflationary |

## Quest: q_recipe_chain

| Original Criterion | Inverted Failure | Surfaced Assumption |
|---|---|---|
| "Compose at least two smaller skills" | "Only one skill used" | Composition is verifiable on disk |
| "Pipeline (supply-chain skill)" | "No pipeline structure" | Pipeline means something specific |
| "Reward: 120 gold" | "Reward not paid" | Gold economy is binding |

## Loadout: chain_verifier_recipe.md

| Original Criterion | Inverted Failure | Surfaced Assumption |
|---|---|---|
| "skill passes gate test" | "skill fails gate test" → implies gate was survivable | Gate is a correct proxy for quality |
| "Fewer skills fail the gate (pre-flight check)" | "Skills still fail after pre-flight" | Pre-flight catches the same failure modes as gate |
| "Fewer buyers get scammed (convergence catches fake quality)" | "Buyers still scammed" | Convergence is detectable pattern |
| "Divergence Lens + Convergence Lens" | "One or both lenses missing" | Lens files exist at expected paths |

## Loadout: inversion_second_order_recipe.md

| Original Criterion | Inverted Failure | Surfaced Assumption |
|---|---|---|
| "Final reframe survives both lenses" | "Reframe still flawed" | Both lenses together capture all significant failure modes |
| "constraint_inversion_lens + second_order_lens" | "Ingredients reference non-existent files" | Ingredients are loadout-present |
| "Epic rarity (both ingredients rare)" | "Ingredients are common rarity" | Rarity labels are accurate |

## Critical Findings

### 1. gate_listed_not_gate_passed Assumption
The chain_verifier_recipe says "skill passes gate test" as a success criterion, but merely listing a skill in loadout does NOT mean it passes the gate. **Assumption: gate pass = loadout listing** — FALSE per standing rules.

### 2. dependency_proof_before_loadout Assumption
The inversion_second_order_recipe requires `constraint_inversion_lens.md` and `second_order_lens.md` from `crafted/`, but the loadout only guarantees files in `loadout/`. **Assumption: crafted/ ingredients are available at boot** — NOT proven.

### 3. composition_proven_before_installation Assumption
Recipes that compose other skills assume the composed skills are proven to exist. **Assumption: skill_path references resolve to real files** — not verified at install time.

### 4. Gold Economy Binding Assumption
Both quests use gold rewards as success conditions. **Assumption: 60g and 120g are meaningful relative to agent wealth** — but if gold is infinite or trivially generated, rewards are hollow.

## Exploit Pattern Discovered

**The Dependency Chain Blind Spot**: A recipe can declare composition with skills NOT in loadout. The chain_verifier_recipe references "Divergence Lens" and "Convergence Lens" but nowhere are these files shown to exist in loadout/. If an agent installs inversion_second_order_recipe without constraint_inversion_lens.md existing, the recipe is broken by design.
