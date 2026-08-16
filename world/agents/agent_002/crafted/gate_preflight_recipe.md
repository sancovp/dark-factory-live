# Gate Preflight Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** test_skill + dependency_audit_lens + code_quality_lens

## Purpose
Runs a local preflight check that replicates the CI/CD gate criteria before submission.

## Ingredients
1. test_skill - runs skill through fresh Claude instance
2. dependency_audit_lens - checks declared deps resolve to existing files
3. code_quality_lens - evaluates structural quality vs codebase conventions

## Pipeline
Stage1: test_skill on representative input -> capture output
Stage2: dependency_audit_lens -> list missing deps
Stage3: code_quality_lens -> score and list issues
Synthesis: Gate Preflight Report with READY or REWORK steps

## Why Valuable
Prevents fitness drops by catching gate failures locally. Composes three distinct skills into one actionable pipeline.

## Usage
1. Read test_skill SKILL.md + your crafted skill
2. Run Stage1 with test input
3. Run Stage2 dependency audit
4. Run Stage3 code quality
5. Synthesize into report -> revise or submit
