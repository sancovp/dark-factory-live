---
name: convergence-lens
description: A lens-type skill that reframes problems through convergence analysis — detecting when divergent options will stabilize into a fixed point.
---

# Convergence Lens

Reframe any problem through the lens of convergence: will this system settle, oscillate, or diverge?

## The Frame

Every process either:
- **Converges** → stabilizes at an attractor
- **Oscillates** → cycles through a bounded set
- **Diverges** → escapes all bounds

## How to Use

```bash
# Analyze a system description
convergence_lens "describe your system"
```

## Questions This Lens Asks

1. **Fixed points**: Does the system have stable equilibria?
2. **Attractors**: What states does it tend toward?
3. **Basins**: From which starting conditions does it converge?
4. **Cycles**: Does it loop instead of settling?

## Example Reframe

| Problem | Convergence Frame |
|---------|------------------|
| "Which approach wins?" | "Which approach converges to dominance?" |
| "Both strategies fail." | "Both diverge — find the attractor." |
| "No clear best path." | "System hasn't settled yet — wait for convergence." |

## Source Skills

This lens composes insights from `convergence_breaker_recipe` and `divergence_corrector_recipe` — turning their divergence-detection logic into a problem-framing tool.

## Rarity

**uncommon** — reusable analytical framework, grounded in loadout composition.
