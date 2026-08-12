---
name: composition-lens
type: lens
rarity: uncommon
description: Reframes any skill by asking how it composes with other skills — reveals structural gaps, chaining opportunities, and what typed inputs/outputs the skill expects.
---

# Composition Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Applies to:** Any skill file (crafted or loadout)

---

## What This Lens Does

Changes how you SEE a skill: not "what does this skill do?" but "how does this skill fit into a larger system?" It forces you to treat every skill as a node in a graph, not a standalone artifact.

---

## The Questions

Apply this lens to any skill by answering ALL of the following:

### 1. INPUT / OUTPUT CONTRACT
- What TYPE of input does this skill expect? (text, structured data, a file path, a previous skill's output?)
- What TYPE of output does this skill produce?
- Are the input/output types EXPLICITLY stated, or assumed?
- If the input type doesn't match what you'd feed it, what breaks?

### 2. ADJACENCY GRAPH
- What other skills could run BEFORE this one? (What feeds it?)
- What other skills could run AFTER this one? (What does it feed?)
- Are there MISSING edges — skills that SHOULD chain to this but don't exist yet?
- Does this skill assume a "default" input that no skill reliably produces?

### 3. TYPED INTERFACE GAPS
- Does this skill declare its SKILL TYPE (Template, Lens, Prosthesis, Recipe, Towering, Combiner)?
- If it declares a type — does its behavior MATCH that type?
- If it doesn't declare a type — does its behavior IMPLY a type?
- Are the gap-filling skills (adjacent nodes in the graph) MISSING from loadout?

### 4. COMPOSABILITY RESISTANCE
- Is this skill self-contained, or does it secretly depend on external tools/scripts?
- Does it assume a specific directory structure?
- Does it embed hardcoded paths that would break if moved?
- Could this skill run in ANY context, or only in the repo where it was written?

### 5. MARKET SIGNAL
- What TYPE of skill would complete the composition chain this skill starts?
- Is there demand (a gap) for that completing skill?
- What rarity would the completing skill need to be?

---

## Output Format

After applying all questions, produce a **Composition Report**:

```
## Composition Report: [skill_name]

### Input/Output Contract
- Input type: [stated/implied/none]
- Output type: [stated/implied/none]
- Gaps: [list]

### Adjacency Graph
- Feeds: [skills that run before]
- Fed by: [skills that run after]
- Missing edges: [gaps in the chain]

### Typed Interface Gaps
- Declared type: [type or none]
- Behavior matches: [yes/no]
- Implied type: [type]

### Composability Resistance
- Self-contained: [yes/partial/no]
- Path hardcoded: [yes/partial/no]
- Portable: [yes/no]

### Market Signal
- Completing skill type needed: [type]
- Rarity recommendation: [rarity]
- Market gap: [yes/no]
```

---

## When to Apply

Apply this lens:
- **Before crafting a new skill** — will it fit into existing composition chains?
- **Before buying a skill** — does it compose with what you already have?
- **Before listing a skill** — does it declare its type and interface clearly?
- **During audits** — does the loadout have gaps in its adjacency graph?

---

## Quality Gate

Apply this lens to the skill itself:
- Does the lens reveal at least 2 concrete gaps or misalignments?
- If no gaps found — is the skill genuinely well-composed, or are you missing something?

A lens that finds nothing on a poorly-composed skill is itself broken.

---

## Rarity Justification

This lens is **Uncommon** because:
- It requires understanding type systems and composition graphs (novel)
- It surfaces gaps that other lenses miss (meta-level, not content-level)
- It has direct market value: pointing to missing skills creates crafting opportunities
