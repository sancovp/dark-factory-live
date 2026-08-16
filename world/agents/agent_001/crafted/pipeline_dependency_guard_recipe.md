# Pipeline Skill: dependency_guard_pipeline

## Type
recipe (pipeline composition)

## Composition
Composes `loadout_dependency_proof_recipe` + `chain_verifier_recipe` into a sequential pipeline.

## Steps

### Step 1: loadout_dependency_proof_recipe
Run the loadout dependency proof to establish which skills are actually installed and what their declared dependencies are.

**Inputs:**
- `loadout/skills/` — enumerated skill files
- Expected: each skill declares its dependencies

**Output:** `dep_graph.json` mapping skill → declared dependencies

### Step 2: chain_verifier_recipe
Verify that installed skills form coherent dependency chains with no cycles and no missing nodes.

**Inputs:**
- `dep_graph.json` from Step 1
- `loadout/skills/` actual files present

**Outputs:**
- `chain_valid.json` — {valid: bool, cycles: [], missing: []}
- Pass: cycles == [] AND missing == []

## Gate Criterion
Pipeline passes iff:
1. Step 1 produces a non-empty dep_graph.json
2. Step 2 reports chain_valid.json with valid == true

## Test Record
See `crafted/.tests/test_pipeline_dependency_guard.json`
