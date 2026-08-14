# Skill Gap Analysis Report

## Stage 1: Extract Dependency Claims

| Skill | Claims |
|-------|--------|
| chain_verifier_recipe.md | Divergence Lens, Convergence Lens |
| inversion_second_order_recipe.md | Constraint Inversion Lens, Second-Order Lens |

## Stage 2: Build Dependency Graph

```
graph TD
  chain --> divergence_lens
  chain --> convergence_lens
  inv2nd --> constraint_inversion_lens
  inv2nd --> second_order_lens
```

- **Hubs**: chain_verifier_recipe (degree=2), inversion_second_order_recipe (degree=2)
- **Orphans**: (none)
- **Dead Ends**: (none)

## Stage 3: Verify Dependencies

| Claimed Skill | Exists? | Status |
|--------------|---------|--------|
| divergence_lens | ❌ MISSING | GAP |
| convergence_lens | ❌ MISSING | GAP |
| constraint_inversion_lens | ❌ MISSING | GAP |
| second_order_lens | ❌ MISSING | GAP |

## Stage 4: Rank Gaps by Value

| Gap | Hub Centrality | Score |
|-----|---------------|-------|
| divergence_lens | 1 (hub=chain_verifier) | 1.0 |
| convergence_lens | 1 (hub=chain_verifier) | 1.0 |
| constraint_inversion_lens | 1 (hub=inv2nd) | 1.0 |
| second_order_lens | 1 (hub=inv2nd) | 1.0 |

## Stage 5: Recommendations

### Gap 1: divergence_lens.md
- **Why needed**: chain_verifier_recipe depends on it
- **Suggested type**: Lens
- **Estimated rarity**: Uncommon
- **Action**: Craft it

### Gap 2: convergence_lens.md
- **Why needed**: chain_verifier_recipe depends on it
- **Suggested type**: Lens
- **Estimated rarity**: Uncommon
- **Action**: Craft it

### Gap 3: constraint_inversion_lens.md
- **Why needed**: inversion_second_order_recipe depends on it
- **Suggested type**: Lens
- **Estimated rarity**: Uncommon
- **Action**: Craft it

### Gap 4: second_order_lens.md
- **Why needed**: inversion_second_order_recipe depends on it
- **Suggested type**: Lens
- **Estimated rarity**: Uncommon
- **Action**: Craft it

## Output Schema

```json
{
  "inventory_size": 3,
  "total_dependency_claims": 4,
  "missing_skills": ["divergence_lens", "convergence_lens", "constraint_inversion_lens", "second_order_lens"],
  "weak_links": [],
  "ranked_gaps": [
    {"gap": "divergence_lens", "score": 1.0, "dependents": ["chain_verifier_recipe"]},
    {"gap": "convergence_lens", "score": 1.0, "dependents": ["chain_verifier_recipe"]},
    {"gap": "constraint_inversion_lens", "score": 1.0, "dependents": ["inversion_second_order_recipe"]},
    {"gap": "second_order_lens", "score": 1.0, "dependents": ["inversion_second_order_recipe"]}
  ],
  "recommendations": [
    {"skill": "divergence_lens", "type": "Lens", "action": "craft"},
    {"skill": "convergence_lens", "type": "Lens", "action": "craft"},
    {"skill": "constraint_inversion_lens", "type": "Lens", "action": "craft"},
    {"skill": "second_order_lens", "type": "Lens", "action": "craft"}
  ]
}
```
