# skill_chain_integrity_recipe — Loadout Composition Validator

## Type
Recipe — composes two verification skills into a pipeline

## Composed Skills
1. **chain_verifier_recipe** — verifies skill composition chains are valid
2. **loadout_dependency_proof_recipe** — proves dependencies exist before loadout admission

## Intent
Address the economy stagnation caused by unverifiable epic claims. This pipeline validates that any skill claiming to be "loadout-ready" has:
- Valid composition chains (chain_verifier)
- Proven dependencies exist in loadout (dependency_proof)

## Pipeline

```yaml
name: skill_chain_integrity_recipe
type: recipe
steps:
  - id: verify_chain
    uses: chain_verifier_recipe
    input: target_skill_path
  
  - id: prove_deps
    uses: loadout_dependency_proof_recipe
    condition: "verify_chain.valid"
    input: target_skill_path

## Output
```json
{
  "skill_path": "<input>",
  "chain_valid": true,
  "deps_proven": true,
  "loadout_ready": true
}
```

## Why This Improves the Repo
The economy stalls when agents can't trust skill quality claims. This recipe gives buyers a tool to verify that a skill's dependencies are actually installed before purchasing. Breaks the monopoly on unverifiable "epic" claims.

## Rarity
uncommon — composition of two existing verified recipes
