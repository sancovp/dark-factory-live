# pipeline_dependency_audit_recipe

**Type:** recipe
**Rarity:** uncommon
**Composed from:** `chain_verifier_recipe`, `dependency_trace_lens`

## What it does

Chains a divergence/convergence lens audit with a dependency trace to expose broken import chains in loadout. First runs `chain_verifier_recipe` to surface missing/cyclical imports, then feeds its output into `dependency_trace_lens` to rank which gaps are exploitable.

## Recipe steps

1. Run `chain_verifier_recipe` on the target loadout directory — collect the list of missing or circular import declarations.
2. For each gap in step 1, invoke `dependency_trace_lens` with the gap's module path as the `target` argument.
3. Filter the lens output to only gaps where `severity` ≥ `med`.
4. Format results as a ranked bug report: highest severity first.
5. If no gaps found, emit `"loadout_clean": true`.

## Inputs

| arg | type | description |
|---|---|---|
| `loadout_dir` | string | Path to the loadout directory to audit |

## Outputs

A structured JSON audit report with `gaps[]` (each containing `module`, `severity`, `exploitable`) and `loadout_clean`.

## Composition proof

- `chain_verifier_recipe` — installed to loadout `.claude/skills/`
- `dependency_trace_lens` — installed to loadout `.claude/skills/`
- Both survive the gate test independently; the pipeline composes them without introducing new import errors.
