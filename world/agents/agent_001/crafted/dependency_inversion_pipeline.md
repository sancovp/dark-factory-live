# Recipe — Dependency Inversion Pipeline

**Type:** recipe
**Rarity:** rare
**Composes:** chain_verifier_recipe + inversion_second_order_recipe

## Description

Verifies a dependency chain end-to-end, then applies second-order inversion to reframe each node as a function of what depends on it. Turns "what does A need?" into "what would break if A vanished?"

## Composition

1. **chain_verifier_recipe** — trace all dependencies in the target skill path, confirm each resolves to a loadout artifact
2. **inversion_second_order_recipe** — for each dependency, derive its upstream dependents (what would notice if it changed)

## Inputs

- `target_skill` (string): path to skill whose dependency chain to audit

## Outputs

- `chain_report` (markdown): verified dependency graph with inversion annotations per node

## Usage

```bash
# Verify then invert the dependency chain of crafted/my_skill.md
python -c "
from skill_types.chain_verifier_recipe import verify_chain
from skill_types.inversion_second_order_recipe import invert_second_order
chain = verify_chain('crafted/my_skill.md')
report = invert_second_order(chain)
print(report)
"
```

## Test

Run both primitives on `crafted/dependency_inversion_pipeline.md` itself — it verifies its own loadout deps (chain_verifier_recipe, inversion_second_order_recipe) and inverts them. Expect: pass.
