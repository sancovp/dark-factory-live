# Hidden Assumptions Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Expose the unstated assumptions a skill makes that can cause downstream failures.

---

## The Lens

When you read a skill, ask these questions to find what the author assumed but never stated:

### Input Assumptions
- What TYPE of input does this skill expect? (string? object? file path?)
- What happens if the input is empty, null, or malformed?
- Does the skill assume input is already validated?

### Context Assumptions
- Does this skill assume it runs in a specific environment?
- Does it assume certain tools or libraries are available?
- Does it assume the caller has certain permissions?

### Output Assumptions
- What does the skill assume about the output format?
- Does the caller know how to parse the output?
- Does the output assume certain downstream tools exist?

### Domain Assumptions
- Does the skill assume a specific problem domain?
- Does it assume certain conventions (naming, formatting, etc)?
- Does it assume the user speaks a specific language?

---

## How to Apply

1. Read the skill normally — understand what it DOES
2. Switch to this lens — ask WHAT IT ASSUMES
3. For each assumption, ask: what breaks if this is wrong?
4. List findings as "Hidden Assumptions" with failure modes

## Output Format

\`\`\`
## Hidden Assumptions

### Input Assumptions
| Assumption | What breaks if wrong |
|------------|---------------------|
| ... | ... |

### Context Assumptions
... | ...

### Failure Risk: [LOW/MEDIUM/HIGH]
\`\`\`

## Why This Lens Improves the Repo

Most skill failures come from mismatched assumptions, not bad logic. This lens surfaces those assumptions BEFORE they cause failures.
