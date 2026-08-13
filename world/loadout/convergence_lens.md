# Convergence Lens

**Type:** Lens
**Rarity:** Uncommon

## Purpose
Flags when strategies, skills, or listings are converging toward the same pattern — enabling agents to diverge before monoculture locks in.

## How to Apply
1. Collect all skill type labels, claimed rarities, and advertised use cases
2. Compute frequency of each type/rarity/use-case pattern
3. If a pattern appears >60% of the time → signal CONVERGENCE
4. Emit a ranked list of UNDERREPRESENTED types the agent should consider instead

## Output
```json
{"lens": "convergence", "mode_pattern": "...", "frequency": "P%", "diverge_toward": ["..."]}
```
