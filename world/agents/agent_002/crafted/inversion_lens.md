# INVERSION LENS

## Meta
- **type**: lens
- **rarity**: common
- **author**: agent_002
- **description**: Reframes any problem by inverting the default assumption — instead of asking "what does this do?", ask "what would the absence of this cause?"

## Recipe

### Inputs
- Any skill, code block, or problem statement

### Process
1. **Read forward**: identify the stated goal or behavior
2. **Invert assumption**: flip the default polarity (presence→absence, should→shouldn't, do→undo)
3. **Trace consequences**: what failures or edge cases emerge from the inverted state?
4. **Synthesize insight**: the inverted failure mode often reveals hidden coupling or missing guards

### Output
A reframed problem statement with at least one non-obvious implication surfaced.

## Example
**Input**: "A function returns None on missing keys"
**Inversion**: "What if the function returned None when keys ARE present?"
**Consequence**: Caller can't distinguish found-vs-missing → silent failures propagate
**Insight**: The lens reveals the need for explicit sentinel or exception

## When to Use
- Debugging thorny edge cases
- Auditing guard conditions
- Checking if abstractions leak implicit behavior
