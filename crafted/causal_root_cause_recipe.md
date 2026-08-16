# Recipe: Causal Root Cause Analysis
Type: Recipe
Output Type: Uncommon
Yield: 1 reusable pipeline for tracing failures back to root causes in skill dependencies

## Ingredients
1. **causation_lens** (Common) — identifies causal mechanisms between components
2. **second-order-lens** (Common) — traces second and third-order effects of failures

## Composition
This recipe chains causation_lens → second-order-lens to create a dependency chain analyzer that:
1. Takes a failing component as input
2. Applies causation_lens to identify what other components it depends on
3. Recursively applies causation_lens to trace the full dependency chain
4. Applies second-order-lens at each link to identify downstream failure propagation
5. Outputs a ranked list of root causes with their propagation paths

## Assembly
```
input: failing_component_path
  → causation_lens (identify immediate dependencies)
  → for each dependency:
      → causation_lens (trace further dependencies)
      → second-order-lens (what breaks downstream if this breaks?)
  → divergence_analyzer (identify which chain link is the true root)
  → output: root_cause_ranking
```

## Input Triggers
- "Component X is broken"
- "Skill Y fails the gate"
- "Dependency Z is missing"
- Any "something doesn't work" where you need to find WHY

## Output Shape
1. **Immediate Cause** — what's directly wrong
2. **Root Cause Chain** — causation_lens output showing dependency path
3. **Second-Order Effects** — second-order-lens output showing cascade if root fails
4. **Root Cause Ranking** — divergence_analyzer output, ranked by:
   - Distance from observed failure (closer = more likely root)
   - Second-order blast radius (wider = higher priority fix)
   - Dependencies count (fewer deps = more likely root cause)

## Quality Check
- Does causation_lens identify at least 2 links before finding root or hitting no-deps?
- Does second-order-lens surface at least 1 effect not obvious from first-order?
- Does the output change your fix priority vs just fixing the immediate cause?

## Example
**Input:** "lens_verify_pipeline fails gate test"

**Processing:**
1. causation_lens → "depends on chain_verifier_recipe + second-order-lens"
2. causation_lens on chain_verifier_recipe → "depends on ??? (missing)"
3. second-order-lens on missing dep → "downstream: pipeline claims valid when invalid; false passes propagate"
4. divergence_analyzer → root cause = chain_verifier_recipe missing from loadout

**Output:** Root cause: chain_verifier_recipe not in loadout (Rank 1), Second-order: false validation confidence (fix immediately)

## Why This Recipe Works
Causation_lens alone gives you "what links here" but not "what breaks if this breaks." Second-order-lens alone gives you "what cascades" but not "where does it start." Chaining them gives you both: trace UP to root, trace DOWN to blast radius, rank by which fix has highest leverage.

## Rarity Justification
- 2 Common ingredients → Uncommon output
- Chain adds temporal reasoning (when in the dependency cycle does failure occur)
- Composition enables analysis impossible with either lens alone
