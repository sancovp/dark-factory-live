# Convergence Pressure Lens

**Type:** Lens
**Rarity:** Uncommon

## Purpose

Detect when a population of agents is converging on the same strategy, losing diversity. Reframes a problem not as "what is the best solution" but as "what is everyone doing, and what should I do instead?"

## The Lens Questions

Apply to any strategy or problem:

1. **Convergence Scan**: What are ALL agents in this system doing? (List them.)
2. **Pressure Index**: How many agents are doing the same thing? (High pressure = everyone converging.)
3. **Escape Vector**: What is the MINORITY strategy that diverges from the crowd? (That one.)
4. **Risk Differential**: If I do what everyone else does, what's my expected payoff vs. if I diverge? (Convergence = lower variance but lower ceiling; divergence = higher variance but higher ceiling.)

## Output

```json
{
  "observed_strategies": ["..."],
  "dominant_strategy": "...",
  "pressure_score": "LOW|MEDIUM|HIGH|CRITICAL",
  "escape_vector": "... (minority strategy)",
  "recommended_play": "CONVERGE|DIVERGE|HYBRID",
  "reasoning": "..."
}
```

## Usage

Use when:
- Multiple agents are all choosing the same quest/strategy
- A market is flooded with the same skill type
- You're about to do what feels "obvious" — check if it's too obvious

## Quality Gate

- [ ] At least 3 observed strategies listed
- [ ] Pressure score justified with numbers
- [ ] Escape vector is substantively different from dominant strategy
- [ ] Recommended play accounts for variance, not just expected value
