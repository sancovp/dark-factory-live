---
name: kbworld_round_improver_recipe
description: "Analyzes a kbworld round report and prescribes fixes using divergence_lens + dependency_lens composition"
version: 0.1.0
---

# kbworld_round_improver_recipe

A recipe that composes `divergence_lens` and `dependency_lens` to diagnose a kbworld round and prescribe actionable improvements.

## When to use

- After any kbworld round completes
- When throughput plateaus or drops
- When no new skills are being encapsulated

## Composition chain

```
round_report.json
    ↓
[divergence_lens] → identifies convergent stagnation
    ↓
[dependency_lens] → identifies missing skill dependencies  
    ↓
[prescription] → generates fix actions
```

## Step-by-step

### Step 1: Gather round state

Read the latest round report from `kbworld/state/rounds/<slug>/report.json`.

Extract:
- `phase_reports`: which phases ran and their outcomes
- `skills_encapsulated`: list of skills generated
- `atoms_admitted`: KB growth metrics
- `issues_filed`: what wrongness was surfaced

### Step 2: Apply divergence_lens

Run the divergence_lens on the round report with input: "Are all agents converging on the same choices?"

Expected output: flags if multiple agents chose identical quests, skills, or accepted the same recipes.

### Step 3: Apply dependency_lens

Run the dependency_lens on `skills_encapsulated` list.

Expected output: flags any skill that references missing dependencies (e.g., a skill that needs `brain_agent` but that dependency isn't in the loadout).

### Step 4: Synthesize prescription

Combine both lens outputs into fix actions:

| Diagnostic | Prescription |
|------------|--------------|
| Convergence detected | File `kb-door` issue to add divergent subject, or switch to cold-target aim |
| Missing dependency | Write gap-filing PR before next round, or create stub skill |
| No encapsulation | Check encapsulate.py `USING_SKILL_TEMPLATE` is rendering, verify `marketplace-entry.json` exists |
| Stalled phase | Inspect that phase's code path, check `Deps` injection is not mocked |

### Step 5: Execute or defer

- If fix is simple (stub, issue): execute immediately
- If fix is structural (phase rewrite): file as `kb-supersede` issue with label `kb-door`

## Example

```bash
# Analyze R3 round
python -c "
from kbworld.round import Round
from pathlib import Path
report = Path('kbworld/state/rounds/r3/report.json')
print(report.read_text())
"
# Then apply divergence_lens + dependency_lens per steps above
```

## Test case

- Input: A round where all agents accepted the same quest type
- Expected: divergence_lens flags convergence, dependency_lens confirms loadout is complete
- Prescription: File kb-door issue for divergent subject

## Dependencies

- divergence_lens.md (from loadout)
- dependency_lens.md (from loadout)
- kbworld/state/ directory must exist
