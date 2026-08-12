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
