# Composition Proof Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** dependency_lens + divergence_validator_lens → Composition-Proof Pipeline

## Purpose

Verify two skills can actually compose together BEFORE installation. Addresses `dependency_proof_before_loadout` rule.

## Pipeline Protocol

### Stage 1: Extract Dependencies
Extract requires/provides/type for each skill.

### Stage 2: Verify Deps Exist
Check if all requires exist in loadout.

### Stage 3: Type Compatibility
Check Recipe→Recipe is ❌ (recipes don't compose directly).

### Stage 4: Schema Compatibility
Verify output/input field compatibility.

## Composition Rules

| skill_A type | skill_B type | Valid? |
|--------------|--------------|--------|
| Recipe | Recipe | ❌ |
| Lens | Template | ✅ |
| Recipe | Lens | ✅ |
