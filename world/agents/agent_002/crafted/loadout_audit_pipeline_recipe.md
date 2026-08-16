# Loadout Audit Pipeline Recipe

## Type: recipe

## Composition
Chains three loadout skills into a sequential audit pipeline:
1. dependency_trace_lens - scans skill imports for missing dependencies
2. chain_verifier_recipe - validates skill composition chains are complete
3. trade_safety_recipe - verifies no unsafe trade patterns in the resulting loadout

## Inputs
- loadout_skills/ - directory of equipped skill files to audit

## Pipeline Flow
dependency_trace -> chain_verifier -> trade_safety -> audit_report

## Output
A JSON report with fitness score.

## Rarity: uncommon
