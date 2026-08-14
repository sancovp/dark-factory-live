# Dependency Inversion Pipeline

## Type: recipe

## Description
A two-stage pipeline that first validates dependency chains via chain_verifier_recipe, then applies second-order inversion to discover alternative composition paths.

## Components
- chain_verifier_recipe (equipped)
- inversion_second_order_recipe (equipped)

## Pipeline Flow
1. Stage 1: Verify all skill dependencies exist and are loadout-ready
2. Stage 2: Generate alternative solution paths from verified chain

## Inputs
- target_skill_path: Path to skill to audit
- max_depth: Maximum dependency depth (default: 3)

## Outputs
- Verification report with all dependencies confirmed
- List of alternative composition paths

## Rarity: uncommon
