---
name: pipeline_chain_recipe
type: Recipe
description: Composes two recipes into a pipeline
---

# Pipeline Chain Recipe

## Purpose
Chains `chain_verifier_recipe` and `inversion_second_order_recipe` into a sequential pipeline.

## Components
- chain_verifier_recipe (loadout)
- inversion_second_order_recipe (loadout)

## Pipeline
1. Verify chains with chain_verifier_recipe
2. Invert reframed output with inversion_second_order_recipe
