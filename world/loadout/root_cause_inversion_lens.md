# Root Cause Inversion Lens

**Type:** lens
**Rarity:** uncommon
**Purpose:** Reframe problems by inverting causality — work backwards from failure to discover hidden root causes

## Description

A reusable analytical lens that reframes problems by tracing backwards from negative outcomes to their hidden causes. Unlike constraint inversion (which flips rules) or second-order analysis (which looks forward), this lens inverts the CAUSAL DIRECTION — treating symptoms as clues and reverse-engineering what must be true for the failure to occur.

## How to Use

Apply this lens BEFORE attempting to solve any problem:
1. State the problem as an observed failure or negative outcome
2. Ask: "What must be TRUE for this failure to occur?"
3. For each necessary condition, ask: "What must be TRUE for THAT to be true?"
4. Continue until you reach a root cause that is actionable
5. The reframed problem is: "Change the root cause, not the symptom"

## Key Questions

1. **Causal Inversion:** If this problem didn't exist, what would be different?
2. **Necessity Test:** What MUST be true for this failure to occur? (Not just correlated, but necessary)
3. **Sufficiency Test:** Is fixing this root cause SUFFICIENT to prevent the failure?
4. **Intervention Point:** Where in the causal chain is intervention most leverageable?

## Output Format

```json
{
  "observed_failure": "<the problem as stated>",
  "necessary_conditions": ["must be true for failure", "..."],
  "root_causes": ["actionable root cause 1", "actionable root cause 2"],
  "reframed_problem": "<the actual problem to solve>",
  "intervention_point": "<where to intervene>"
}
```

## Example Application

**Problem:** "The skill keeps failing the gate test"

**Root Cause Inversion:**
- Necessary condition 1: The skill doesn't match gate criteria
- Necessary condition 2: Gate criteria aren't documented in the skill
- Root cause: Skill was written without reading gate requirements
- **Reframed problem:** "Read gate requirements BEFORE crafting"

## Why This Lens Is Different

- **Constraint inversion** flips RULES (must → must not)
- **Second-order lens** traces FORWARD effects of actions
- **Root cause inversion** traces BACKWARD from failures to causes

## Composition

Self-contained lens; applies to any problem without composing other skills.

## Quality Check

Apply this lens to a known failure. If the reframed problem points to a different solution than the original, the lens is working. If reframing produces the same answer, the original problem statement was already well-formed.
