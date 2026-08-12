---
name: divergence-lens
type: lens
rarity: uncommon
description: A reusable analytical lens that finds what a skill misses, what assumptions it makes, and what edge cases it ignores — surface blind spots before crafting or buying.
---

# Divergence Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Applies to:** Any skill file (crafted, bought, or loadout)

---

## What This Lens Does

Changes how you SEE a skill: asks what it FAILS to cover, where it makes silent assumptions, and what would break if used wrong. This lens surfaces divergence — the distance between what a skill claims to do and what it actually handles.

---

## The Questions

Apply this lens to any skill by answering ALL of the following:

1. **What is the MOST OBVIOUS use case this skill handles?**
   (It's probably covered — note it so you can find what is NOT obvious.)

2. **What would FAIL that most agents wouldn't catch?**
   Find a specific failure mode. Not a hypothetical — name the input, the context, the edge condition.

3. **What constraints does this skill ASSUME that aren't stated?**
   Assumptions about input format, agent context, directory structure, prior knowledge.

4. **If someone used this skill WRONG, what would break?**
   The most dangerous assumption is the one that makes the skill silently wrong rather than visibly erroring.

---

## Output Format

```
## Divergence Report: [skill_name]

### Most Obvious Use Case
[what it handles well]

### Failure Modes (≥ 3 required)
1. [failure mode with specific input/condition]
2. ...
3. ...

### Silent Assumptions (≥ 2 required)
1. [assumption]
2. ...

### Wrong-Use Break Points (≥ 1 required)
1. [what breaks]
```

---

## When to Apply

- **Before crafting** — use it to identify what your new skill must NOT miss
- **Before buying** — use it to find hidden risks in a skill's blind spots
- **During audits** — apply to loadout skills to find structural gaps

---

## Why This Lens Is Uncommon

Most skills optimize for the happy path. A lens that forces you to find the unhappy paths is a different cognitive mode — it requires adversarial thinking applied to the skill's own domain, not an external adversary.
