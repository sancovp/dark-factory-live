# Entropy Lens

**Type:** Lens  
**Rarity:** Rare  
**Skill ID:** entropy_lens

## The Problem

Agents optimize for what they can see: structure, lines of code, test coverage. But the most dangerous failures are invisible — the entropy that builds silently in a codebase. This lens reframes every problem as a question of information entropy.

## How It Works

Every codebase element can be examined along entropy dimensions:

1. **Shannon Entropy** — How unpredictable is this? (high entropy = more information content)
2. **Thermal Entropy** — How much disorder has accumulated? (tech debt, duplication, inconsistency)
3. **Cross-Entropy** — How far is current state from ideal state?

## The Reframe

For any input problem P, apply this transformation:

**Step 1: Calculate current entropy**
- What is the current information content of this system?
- How ordered or disordered is it?

**Step 2: Identify entropy sources**
- What is adding disorder?
- What is consuming information content?

**Step 3: Find the entropy sink**
- Where is energy being dissipated without producing leverage?
- What would reducing entropy here compound most?

**Step 4: Reframe the problem**
Original: "How do I fix X?"
Entropy: "Where is entropy building fastest, and what would reduce it most?"

## Output Schema

```
## Entropy Analysis

### Current Entropy: [low/medium/high]
### Entropy Sources: [list]
### Entropy Sink: [where energy dissipates]
### Reframed Problem: [the entropy question]
### Entropy Reduction Vector: [where to act]
```

## Example

Input: "The documentation is outdated"

Entropy analysis:
- Current Entropy: HIGH (docs disagree with code)
- Entropy Sources: no doc-tests, manual authoring, no sync mechanism
- Entropy Sink: developer time spent reconciling docs vs reality
- Reframed: "How do I reduce entropy drift between docs and code?"
- Entropy Reduction Vector: doc-tests that fail when docs diverge from implementation

## Quality Gate

- [ ] Entropy dimension identified (Shannon/thermal/cross)
- [ ] At least 2 entropy sources listed
- [ ] Entropy sink is specific and actionable
- [ ] Reframed problem is substantively different from original
- [ ] Reduction vector is concrete

## Rarity Justification

Rare because:
- No existing lens applies information theory to codebase problems
- Entropy frame surfaces failures invisible to structural analysis
- Guides toward self-reinforcing improvements (reduce entropy once → compound benefits)
- Applicable to any domain (code, docs, tests, architecture, process)
