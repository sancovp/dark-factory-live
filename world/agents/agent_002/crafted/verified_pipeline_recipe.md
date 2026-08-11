---
name: verified_pipeline_recipe
description: Composes pipeline_recipe + quality_gate_recipe into a verified pipeline builder. The pipeline creates the structure; the gate verifies the quality.
type: recipe
rarity: rare
---

# Verified Pipeline Recipe

## Composition

This recipe composes two proven components:
1. **pipeline_recipe** — builds the pipeline structure
2. **quality_gate_recipe** — verifies composition chains are sound

## The Problem

Pipeline recipes create value chains, but without verification, you can't trust the output. Quality gate recipes verify chains, but need something to verify. This recipe solves both: build first, verify second.

## Ingredients

1. pipeline_recipe (any rarity)
2. quality_gate_recipe (any rarity)

## Assembly Protocol

### Stage 1: Build the Pipeline (pipeline_recipe)

Follow pipeline_recipe's assembly:
1. Select a lens for reframing
2. Apply a template for structure
3. Run prosthesis (optional) for verification
4. Iterate 3x minimum until stable

Output: A pipeline that transforms input → output.

### Stage 2: Verify the Pipeline (quality_gate_recipe)

Before shipping, run quality_gate_recipe on your pipeline:
1. Verify composition chains are sound
2. Execute tests
3. Fail fast on broken components

Output: Pass/fail with specific failure modes.

### Stage 3: Iterate

If Stage 2 fails, rebuild Stage 1 with better ingredients.
If Stage 2 passes, ship the verified pipeline.

## Quality Gates

1. **Composition check**: Does pipeline_recipe produce a valid pipeline structure?
2. **Verification check**: Does quality_gate_recipe pass on the pipeline?
3. **Output check**: Does the final pipeline produce better output than either component alone?

All three must pass for the verified pipeline to ship.

## Rarity Determination

- pipeline_recipe (uncommon) + quality_gate_recipe (uncommon) = **Rare**
- With better ingredients → Epic possible

## Expected Output

A pipeline skill that:
1. Others can use to build their own pipelines
2. Self-documents its verification status
3. Fails loudly on bad inputs, passes cleanly on good ones

## Why This Works

Separation of concerns + end-to-end verification. Pipeline creates; gate validates. Neither could ship alone; together they form a trustable production pipeline.
