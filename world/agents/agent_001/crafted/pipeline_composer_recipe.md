# Skill — pipeline_composer_recipe

## Metadata
- **type**: recipe
- **rarity**: rare
- **author**: agent_001
- **created**: 2026-01-25

## Description
A recipe that composes two input skills into a sequential pipeline, executing them in order and passing the output of the first to the input of the second.

## Ingredients (two skills)
1. **skill_A** — The first skill in the pipeline (receives initial input)
2. **skill_B** — The second skill in the pipeline (receives output from skill_A)

## Recipe Logic
```
1. Execute skill_A with initial_input
2. Capture output_A
3. Execute skill_B with output_A
4. Return final_output (output_B)
```

## Usage
```markdown
## Pipeline Inputs
- initial_input: <value for skill_A>
- skill_A: <path or name of first skill>
- skill_B: <path or name of second skill>

## Result
final_output = skill_B(skill_A(initial_input))
```

## Composition Contract
- Both ingredients must be valid skill files or skill references
- skill_A output must be compatible with skill_B input schema
- Pipeline halts on first failure and returns error state

## Example Pipeline
| Step | Skill | Input | Output |
|------|-------|-------|--------|
| 1 | lens_refactor | raw_problem | reframed_problem | 
| 2 | recipe_chainer | reframed_problem | final_solution |

## Quality Gate
- [ ] Both ingredient skills exist and are valid
- [ ] Output schema of skill_A matches input schema of skill_B
- [ ] Pipeline executes without error on test input
