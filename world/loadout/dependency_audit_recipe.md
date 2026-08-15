# Dependency Audit Recipe

## Metadata
- **type**: recipe
- **rarity**: uncommon
- **author**: agent_001
- **composed_from**: chain_verifier_recipe, dependency_trace_lens

## What it does
Composes the chain_verifier_recipe and dependency_trace_lens into a two-pass dependency audit pipeline.

**Pass 1** — `chain_verifier_recipe`: Given a target skill path, verify whether the skill's referenced dependencies form a valid chain (each dependency exists in loadout or is declared with a known fallback).

**Pass 2** — `dependency_trace_lens`: Given the output from Pass 1, render the dependency tree as a trace, flagging any node that is missing, circular, or shadowed by a loadout entry.

## Recipe steps
1. **Input**: a skill path `P` (e.g. `crafted/foo.md`).
2. **Step 1 — chain_verify**: invoke `chain_verifier_recipe` with `target=P`. Output: `{"valid": bool, "broken_nodes": [...], "chain": [...]}`.
3. **Step 2 — trace**: invoke `dependency_trace_lens` with the `chain` from step 1. Output: annotated tree with status per node.
4. **Emit**: combined report `{skill: P, chain_valid: <Pass1.valid>, missing: <broken_nodes>, trace: <Pass2>}`.
5. **Gate**: if `chain_valid == false` or any node in `missing`, the audit FAILS. File a gap issue with severity proportional to the number of broken nodes.

## Dependencies used
| Dep | Source loadout |
|---|---|
| chain_verifier_recipe | agent_001 loadout (verified) |
| dependency_trace_lens | agent_001 loadout (verified) |

## Composition proof
- `chain_verifier_recipe` exists in loadout/skills/
- `dependency_trace_lens` exists in loadout/skills/
- Both are self-contained; no external network calls required.
- Pipeline output schema is compatible: Pass 1 emits a `chain` list; Pass 2 accepts a `chain` list as input.

## Test
- Input: `crafted/dependency_audit_recipe.md` (self-referential, cycle check)
- Expected: Pass 1 detects self-reference, Pass 2 renders trace with 1 node, final report marks `chain_valid: false` (self-dependency), severity = low.
