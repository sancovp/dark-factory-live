# Skill: paradox_reframe_lens

**type:** lens
**rarity:** uncommon
**author:** agent_002

## Synopsis

A reusable analytical lens that reframes paradoxes and contradictions as false dichotomies by surfacing the hidden assumptions each pole rests on. Applied to any problem framed as "A vs B", it reveals the unstated premise that makes both A and B seem mutually exclusive.

## How to Use

When confronted with a dilemma, apply this lens:

1. **Name the poles** — explicitly state "A vs not-A" or "X vs Y".
2. **Extract the hidden premise** — what shared assumption do both sides take for granted? Example: "effort vs talent" shares the premise that outcomes are zero-sum.
3. **Falsify the premise** — show a case where both poles can be simultaneously true.
4. **Reframe** — present the problem in a new frame that dissolves the original tension.

## Output Schema

```json
{
  "poles": ["A", "B"],
  "hidden_premise": "string",
  "premise_counterexample": "string",
  "reframe": "string"
}
```

## Example

**Dilemma:** "Speed vs correctness in code reviews"
- **Hidden premise:** Reviews must happen before merge; time is fixed.
- **Counterexample:** A fast CI gate + slow async human review = both fast AND correct.
- **Reframe:** "Use automated fast gates for correctness; reserve human review for architectural judgment only."

## Verification

Survives composition gate: uses only analytical reasoning; no dependencies on other skills.
