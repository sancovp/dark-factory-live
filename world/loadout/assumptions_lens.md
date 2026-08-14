# Assumptions Lens

**Type:** Lens
**Rarity:** Uncommon
**Description:** A reusable analytical lens that surfaces the hidden assumptions behind any problem, statement, or proposed solution. Every argument rests on unstated premises — this lens exposes them for scrutiny.

## Input
```json
{"subject": "<string>", "context": "<optional string>"}
```

## How to Apply the Lens

1. **Extract the claim** — What is the main statement or proposed action?
2. **Identify explicit constraints** — What conditions are stated as facts?
3. **Surface hidden premises** — What MUST be true for the claim to hold?
4. **Test each premise** — Is each assumption justified?
5. **Flag invalid assumptions** — What happens if an assumption is wrong?

## Questions to Ask

- What does this assume to be TRUE that is NOT stated?
- What does this assume will NOT change?
- What does this assume about human behavior?
- What does this assume about the system it operates in?
- What would BREAK if any assumption is false?

## Output
```json
{
  "claims": ["<main statement>"],
  "explicit_constraints": ["<stated conditions>"],
  "hidden_assumptions": ["<unstated premises>"],
  "assumption_risks": [{"assumption": "...", "if_wrong": "...", "severity": "high/med/low"}],
  "refined_statement": "<claim with assumptions made explicit>"
}
```

## Usage Example

**Input:** "We should migrate to the cloud to save money."

**Analysis:**
- Hidden assumption: Cloud costs < current infrastructure costs
- Hidden assumption: Performance will meet requirements
- Hidden assumption: Migration effort is manageable
- Hidden assumption: Vendor lock-in is acceptable

**Refined statement:** "We should migrate to the cloud IF cloud costs remain < current costs AND performance meets requirements AND migration effort is acceptable AND vendor lock-in is acceptable."

## Why This Lens Improves the Repo

- Forces explicit reasoning about what we assume to be true
- Prevents decisions based on unexamined premises
- Complements Divergence Lens (examines alternatives) and Convergence Lens (examines patterns)
- Creates better problem statements by making hidden beliefs visible
