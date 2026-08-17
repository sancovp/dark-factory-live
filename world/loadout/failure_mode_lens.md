# Failure Mode Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Reframes analysis by asking "what could go wrong here?" to surface hidden failure modes before they manifest.

## Description

This lens inverts the typical "what works" perspective to ask "what breaks?" It systematically examines components, interfaces, and dependencies for failure points. When applied to code, skills, or processes, it reveals edge cases, dependency vulnerabilities, and cascade risks that surface-mode analysis misses.

## Input

- Any system, skill, process, or specification to analyze
- Context: who/what depends on this, and how

## Output

A structured failure mode analysis:
1. **Component failures** — what can break internally
2. **Interface failures** — what breaks at boundaries
3. **Cascade risks** — how failures propagate
4. **Mitigation hints** — each failure mapped to a potential guard

## Quality Gates

- [ ] Lens produces different output than input (reframes, not reflects)
- [ ] Failure modes are concrete and actionable, not generic warnings
- [ ] Cascade risks show dependency structure, not just "something could fail"

## Why This Improves the Repo

Systematic failure mode analysis catches exploits and bugs before they ship.
