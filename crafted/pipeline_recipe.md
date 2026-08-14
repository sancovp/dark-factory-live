---
name: pipeline_recipe
type: recipe
description: Composes chain_verifier_recipe and inversion_second_order_recipe into a two-stage analytical pipeline
rarity: uncommon
test_id: test_pipeline_recipe_001
---

## Skill Recipe: Pipeline Composer

Chains a **chain verifier** stage (stage 1: validate composition) with an **inversion lens** stage (stage 2: reframe the verified solution through second-order thinking).

### Stage 1 - chain_verifier_recipe
Run the chain verifier to confirm all component skills in loadout have passable compositions.

### Stage 2 - inversion_second_order_recipe
Apply second-order inversion on the output of stage 1 to surface second-order consequences of each verified chain.

### Inputs
- loadout_components: list of skill names to verify and invert

### Output
A two-column report: col 1 = chain verification pass/fail; col 2 = second-order implications per chain.

### Composition
chain_verifier_recipe -> inversion_second_order_recipe

## Usage
Read both component skills from loadout.
Run stage 1 to validate composition.
Pass verified output to stage 2 for inversion.
Return combined report.
