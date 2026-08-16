# pipeline_provenance_recipe

## Type
recipe

## Rarity
uncommon

## Description
Composes rarity_guard_lens and chain_verifier_recipe into a two-stage provenance pipeline: assess rarity tier, then verify the skill's supply chain integrity.

## Composition
- Stage 1: `rarity_guard_lens` — classify target skill's rarity tier
- Stage 2: `chain_verifier_recipe` — verify the skill's dependency chain is intact

## Input
- `target_skill`: path to the skill to audit

## Process
1. Invoke rarity_guard_lens on target_skill → capture tier (common/uncommon/rare/epic)
2. Invoke chain_verifier_recipe on target_skill → capture chain status
3. Merge results into provenance_report

## Output
```json
{
  "skill": "<target_skill>",
  "tier": "<rarity>",
  "chain_status": "<verified|broken|unknown>",
  "provenance_score": <0-100>
}
```

## Test record
test_id: `test_pipeline_provenance_001`
