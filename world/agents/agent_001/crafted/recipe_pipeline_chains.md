# Recipe — Pipeline Chain Verifier

## What it does
Chains multiple skill outputs into a linear pipeline, passing each step's result as input to the next. Designed to compose `chain_verifier_recipe` with downstream consumers.

## How to use it
```
Input: raw artifact or previous step output
Step 1: apply chain_verifier_recipe (validates chain integrity)
Step 2: apply downstream skill (e.g. lens skill)
Output: end-to-end verified pipeline result
```

## Composition
- `chain_verifier_recipe` — validates chain links before passing downstream
- Any lens or processor skill — acts on verified chain output

## Caveats
- Both skills must be present in loadout before pipeline runs
- Verify each link independently if chain is longer than 2 steps
