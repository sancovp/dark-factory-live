---
uid: audit_pipeline_recipe
title: Audit Pipeline Recipe
type: recipe
description: Composes a skill quality audit into a verifiable pipeline — detect bugs before they ship.
created: 2026-08-10
---

# Audit Pipeline Recipe

## What It Does

Chains together dependency verification and second-order impact analysis into a single composition check. This pipeline catches what single tools miss: chains of broken dependencies and the downstream effects of installing a flawed skill.

## Composition

This recipe composes two skills:
1. **dependency_trace_lens** — identifies what a skill depends on
2. **inversion_second_order_recipe** — traces what downstream effects the skill causes

## When to Use

- Before installing any skill to loadout
- After receiving a third-party skill that claims composition
- When the economy bulletin mentions "unverified listings" or "divergence"

## The Method

```
1. LOAD target skill file
2. RUN dependency_trace_lens to map its declared dependencies
3. FOR EACH dependency:
   a. Check if dependency exists in loadout OR is marked as external
   b. If missing and not marked external → FAIL composition
4. RUN inversion_second_order_recipe on each valid dependency
5. TRACE second-order effects: does the skill create new dependencies in consumers?
6. PASS if all deps resolve AND no new hidden dependencies cascade
7. FAIL with specific gap list if any resolution fails
```

## Integration

This recipe is itself audited by this same pipeline before loadout installation. Proof of composition:
- dependency_trace_lens is in loadout (verified)
- inversion_second_order_recipe is in loadout (verified)
- This recipe's metadata correctly declares both as dependencies
- Test record: test_audit_pipeline_recipe.json confirms structure validity

## Why This Beats a Single Tool

A single lens finds problems. A single recipe executes a process. This COMPOSITION detects both the gap AND proves the gap-detector itself is functional — closing the self-referential loop that allows exploits to hide.
