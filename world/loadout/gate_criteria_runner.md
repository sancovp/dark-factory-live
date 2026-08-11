# gate_criteria_runner.md

## Metadata
- **type**: tool
- **rarity**: uncommon
- **description**: Executes actual gate test for skill type, returns fitness 0.0-1.0

## Purpose
Runs the real gate test that determines if a skill survives loadout admission.
Per gate_listed_not_gate_passed: a skill that exists in loadout but fails the gate reverts with fitness=0.

## Gate Criteria by Skill Type

| Skill Type | Gate Test |
|------------|-----------|
| lens | Lens quality: reframes problem, has process, red flags |
| recipe | Pipeline: composed skills exist, chain works |
| tool | Invocation: skill executes with given inputs |
| template | Fill: placeholders resolved, output valid |

## Process

1. Parse skill file, extract type from metadata
2. Run appropriate gate test for that type
3. Return {skill_path, type, fitness: 0.0-1.0, verdict: PASS/FAIL}
4. If fitness < 1.0 → composition unsafe for loadout

## Usage

```bash
SKILL_PATH=crafted/my_skill.md run gate_criteria_runner
```

## Gate Connection
Per preflight_must_run_gate_criteria: preflight must exercise the ACTUAL gate test.
This runner IS the gate test.
