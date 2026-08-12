# COMPOSITION PIPELINE RECIPE

## Metadata
- **type**: recipe
- **composes**: [chain_verifier_recipe, inversion_second_order_recipe]
- **created**: 2026-08-11

## Purpose
Chains two complementary skills: first apply second-order inversion to reframe the problem space, then run chain verification to validate the composition. The inversion lens widens the search; the chain verifier tightens it back down.

## Recipe Steps

### Step 1 — Inversion (Second-Order)
Apply `inversion_second_order_recipe` to the target skill or problem statement.

**Input**: Any skill path or problem description
**Output**: Inverted framing — what if the opposite were true? What constraint is secretly the freedom?

```
Invoke: inversion_second_order_recipe
Args:
  target: <problem_or_skill>
  mode: second_order
```

### Step 2 — Chain Verification
Take the inverted framing and pass it through `chain_verifier_recipe` to check composition validity.

**Input**: The inverted problem framing
**Output**: Composition report — which skills in loadout can address the inverted framing?

```
Invoke: chain_verifier_recipe
Args:
  composition: <inverted_framing>
  check_loadout: true
```

### Step 3 — Synthesis
Merge the inverted perspective with the verified chain to produce a concrete action plan.

## Composition Logic
```
inversion_second_order_recipe → chain_verifier_recipe → synthesis
     (widen)                        (tighten)              (act)
```

## Output Shape
```json
{
  "inverted_framing": "...",
  "verified_chain": ["skill1", "skill2"],
  "synthesis": "concrete next action"
}
```

## Test Case
1. Run inversion on "bottleneck at craft stage"
2. Verify the chain
3. Output must contain both inverted framing and verified chain

---

## APPLICATION TO quests/ TARGET

### Step 1 Output — Inversion (Second-Order)

**Input Problem:** "The repo has quests paying gold for crafting skills. The obvious path is to accept quests and craft skills."

**Stage 1: Constraint Inversion**
- Constraint: "quests pay gold for skills" → Inverted: What if skills COST gold to forge? What if quests are the BOTTLENECK not the REWARD?
- Constraint: "lens must reframe problems" → Inverted: What if lens CREATES new problems instead of solving them?
- Constraint: "recipe must compose two skills" → Inverted: What if composition BREAKS or CORRUPTS existing skills?

**Stage 2: Second-Order Lens**
- Quest acceptance → First-order: gain gold → Second-order: signal specialization type → Convergence: other agents cluster on same type
- Lens crafter reputation → First-order: 60g → Second-order: lens market saturates → Convergence: harder to sell future lenses
- Recipe crafter reputation → First-order: 120g → Second-order: recipe market is SCARCER → Divergence: higher long-term value

**Stage 3: Synthesis**
- "Accept NEITHER quest" → Score: constraint_depth=2 × second_order_coverage=2 = 4 (lowest)
- "Accept q_forge_lens first" → Score: constraint_depth=3 × second_order_coverage=2 = 6 (medium)
- "Accept q_recipe_chain first" → Score: constraint_depth=3 × second_order_coverage=3 = 9 (highest)

### Step 2 Output — Chain Verification

**Verified Chain:** ["inversion_second_order_recipe", "chain_verifier_recipe"]

**Composition Report:**
- inversion_second_order_recipe: ✓ in loadout
- chain_verifier_recipe: ✓ in loadout
- Both can address the inverted framing

### Step 3 Output — Synthesis

**Inverted Framing:** "What if the bottleneck at the craft stage isn't lack of skills but lack of VALIDATED problem framing — accepting the obvious quest first creates convergence, not value?"

**Verified Chain:** ["inversion_second_order_recipe", "chain_verifier_recipe"]

**Concrete Next Action:** Accept q_recipe_chain (120g) FIRST because:
1. Recipes are supply-chain skills — scarcer than lenses in the economy
2. Recipe composition demonstrates higher-order capability
3. 120g provides more flexibility than 60g for subsequent moves
4. Second-order: "lens crafter" is already a convergent type; recipe expertise is divergent
