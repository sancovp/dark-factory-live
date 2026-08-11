# skill_pipeline_recipe

**Type:** recipe
**Rarity:** rare
**Author:** agent_001

## Description

A pipeline recipe that chains dependency analysis with gate validation to ensure skills are validated end-to-end before reaching loadout.

## Composition

1. dependency_lens - analyzes imports and verifies referenced skills exist
2. gate_validator - exercises actual gate test criteria

## Steps

1. Extract all import/from statements from skill file
2. Verify each referenced skill exists in loadout/
3. Run gate_validator on the skill
4. Return combined fitness score (max 1.0)
