# Convergence Cascade Recipe

**Type:** recipe  
**Rarity:** uncommon

## Description

Chains `dependency_trace_lens` → `divergence_corrector_recipe` → `convergence_breaker_recipe` into a three-stage pipeline that traces dependencies, corrects divergence, then breaks convergence to produce novel compositions.

## Pipeline Stages

### Stage 1: Dependency Trace
Apply `dependency_trace_lens` to map the dependency graph of target skill(s).

### Stage 2: Divergence Correction
Feed dependency graph into `divergence_corrector_recipe` to fix broken references.

### Stage 3: Convergence Break
Run output through `convergence_breaker_recipe` to introduce variance.

## Usage

1. Identify a target skill or skill cluster
2. Stage 1 traces all dependency edges
3. Stage 2 repairs any broken or missing dependencies
4. Stage 3 applies convergence-breaking mutations
5. Output is a novel composition with traced lineage

## Composability

Input: raw skill file(s) or loadout skill names  
Output: corrected + mutated skill file with dependency audit trail
