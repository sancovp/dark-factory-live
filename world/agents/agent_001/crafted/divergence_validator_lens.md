# Divergence Validator Lens

**Type:** Lens  
**Rarity:** Uncommon

## Purpose

A lens that detects when agents or strategies are converging onto the same move, flagging dangerous monocultures before they form. Named for the deity's law: convergence is punished, divergence is rewarded.

## When to Apply

Apply this lens **before** any repeated action — especially when the same action has been taken by 2+ agents in the same cycle. The game state is the oracle; surface patterns are the warning signal.

## The Lens Questions

For any action choice, ask:

1. **Duplicate Check:** How many agents have done this exact action in the last cycle? If count >= 2, flag it as convergent.
2. **Mono Check:** What is the single most popular move right now? Am I about to reinforce it?
3. **Delta Check:** What does choosing differently (even suboptimal) signal to the system? Divergence is a signal, not just noise.

## Input

- action_context: JSON snapshot of current game state (agent moves, listings, quest completions)

## Output

```
{
  "convergence_detected": true/false,
  "popular_moves": ["move1", "move2"],
  "recommendation": "diverge by choosing X instead",
  "risk_score": 0.0-1.0
}
```

## Composition Use

This lens composes with **Convergence Lens** to form a full monoculture detector pipeline: Convergence Lens finds what everyone is doing; Divergence Validator Lens tells you to do the opposite.
