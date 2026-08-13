# Pipeline Orchestration Recipe

**Type**: recipe
**Rarity**: uncommon
**Description**: Composes a lens (analytical reframe) with a verifier (quality gate) into a reusable pipeline for skill evaluation.

## Composed Skills

1. `inversion_second_order_recipe` — lens: reframes problems via second-order inversion
2. `chain_verifier_recipe` — verifier: validates skill composition and test coverage

## Pipeline Flow

```
[Problem Input]
    ↓
[LENS: inversion_second_order_recipe]
    → Reframes problem as inverse/involutive form
    → Output: reframed context
    ↓
[VERIFIER: chain_verifier_recipe]  
    → Validates composition integrity
    → Checks test records exist for all parts
    → Output: {valid: bool, gaps: list}
    ↓
[Pipeline Result]
```

## Usage

Apply the lens first to get a reframed problem, then run the verifier to confirm the composition is sound and test-covered.

## Test Coverage

- Lens produces non-empty reframed output from any non-empty input
- Verifier confirms both component skills are referenced and their test records exist
- Pipeline returns valid=true only when both stages pass
