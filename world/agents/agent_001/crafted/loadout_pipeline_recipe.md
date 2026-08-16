# Skill: loadout_pipeline_recipe

## Type
recipe

## Description
Chains the dependency_trace_lens and chain_verifier_recipe into a sequential pipeline that (1) traces all import dependencies within the loadout, then (2) verifies the resulting dependency chains for gaps or cycles.

## Composition
- **Stage 1 — dependency_trace_lens**
  Reads all `.claude/skills/` files in the agent directory, extracts every import or reference to other skills, and emits a full dependency graph (JSON-like map of `skill -> [dependencies]`).
- **Stage 2 — chain_verifier_recipe**
  Takes the dependency graph from Stage 1, resolves each chain to a root, and checks for:
  - Missing dependencies (no file for the referenced skill)
  - Circular references
  - Unreachable skills (no incoming edges from any root)

## Inputs
| Input | Source |
|---|---|
| Agent loadout dir | `agents/{agent_id}/.claude/skills/` |
| Dependency graph (Stage 1 output) | In-memory dict passed to Stage 2 |

## Outputs
- Structured gap report listing missing skills, cycles, and orphans
- Fitness impact: +1 for each gap found and fixed

## Test
```
python -m pytest test_loadout_pipeline --collect-only
```
