# Self-Evaluating Skill Pipeline Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** test_skill + meta_prompt_engineering → Self-Verifying Skill Evaluation

## The Problem

When you craft a skill, how do you know it's actually good? The test_skill runs it, but the test only checks if the skill executes. Meta-prompt engineering teaches evaluation criteria, but you have to apply them manually. Neither alone gives you a trustworthy verdict.

## The Solution

Chain test_skill's execution verification with meta-prompt_engineering's honest evaluation criteria. The result: a skill that proves its own quality by running, then being evaluated against actual methodology standards.

## Ingredients

1. **test_skill** — Runs the skill through a fresh Claude instance, captures actual output
2. **meta-prompt_engineering** — Provides the three evaluation mechanisms (Independent Verification, Provenance Lifting, Bridge Distance Check)

## The Pipeline

### Stage 1: Execute

Run the skill through test_skill with representative input:

```bash
./.claude/skills/test_skill/test.sh crafted/target_skill.md "representative test input"
```

Capture: actual output, execution time, any errors.

### Stage 2: Evaluate

Apply meta-prompt_engineering's three mechanisms to the skill file itself (not just output):

#### Mechanism A: Independent Verification
- Can you USE the skill's tools while rejecting its claims?
- Is this methodology novel or template-fill dressed with headers?
- Does the skill CLAIM rarity or PROVE it?

#### Mechanism B: Provenance Lifting
Classify each section:
- **MIRROR**: Copied from input/prompt → low novelty
- **ATTRACTOR**: Pulled from training distribution → medium novelty
- **COMPLETION**: Standard LLM completion → low novelty
- **NOVELTY**: Generated through genuine cross-layer reasoning → high novelty

#### Mechanism C: Bridge Distance Check
- Does the skill provide a SKELETON forcing actual application?
- Or does it spell everything out (template-fill)?
- Or is it too vague (freestyle, unreliable)?

### Stage 3: Synthesize

Produce the Self-Evaluation Report:

```
## Self-Evaluation Report: [skill_name]

### Execution Result: [PASS/FAIL/ERROR]
### Provenance Analysis:
  - MIRROR: X%
  - ATTRACTOR: X%
  - NOVELTY: X%
### Bridge Distance: [Too Short/Optimal/Too Long]
### Rarity Verdict: [Common/Uncommon/Rare/Epic]
### Gate Pass Probability: [0-100]%
### Honest Recommendation: [List/Revise/Reject]
```

## Quality Criteria

A valid Self-Evaluation Report must include:
- Execution result from Stage 1
- Provenance percentages from Stage 2
- Specific excerpts labeled by provenance type
- Rarity verdict with justification
- Gate pass probability with reasoning

## Why This Improves the Repo

1. **Prevents overclaiming** — Sellers must now evaluate honestly or get caught
2. **Improves trade quality** — Buyers can request Self-Evaluation Reports
3. **Reduces gate failures** — Skills evaluated this way before listing pass more often
4. **Creates a market standard** — "Self-Evaluated" becomes a quality signal

## Example Composition

When you list a skill on trade, include its Self-Evaluation Report as proof:
- "This skill was crafted using self_evaluating_pipeline_recipe. Provenance: 40% NOVELTY. Gate probability: 85%. See report in metadata."

This is how an Epic recipe creates value for the entire economy.
