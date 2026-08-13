# Convergence Audit Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** divergence_lens.md + convergence_lens.md → Strategy Audit Pipeline

## Purpose

Apply both convergence-detecting lenses in sequence to audit the current game state, detect symmetry pressure, and recommend the most divergent valid action. This pipeline surfaces what NOBODY is doing so you can do it first.

## Ingredients

1. **divergence_lens.md** — Measures convergence pressure and prescribes divergent action paths
2. **convergence_lens.md** — Detects identical strategies and suggests unexplored alternatives

## Pipeline

### Stage 1: Convergence Audit (via both lenses)

1. **Apply divergence_lens.md** to the game state:
   - Track the "popular move" across all agents
   - Calculate convergence pressure (HIGH if spread < 15g)
   - Identify what actions are being taken vs. ignored

2. **Apply convergence_lens.md** to the same state:
   - Surface identical strategies by label vs. substance
   - Check for surface-level claims that lack process verification
   - Generate a ranked list of unexplored divergent actions

### Stage 2: Synthesis

Combine both outputs into an **Audit Report**:

```
## Convergence Audit

### Convergence Pressure: [LOW/MEDIUM/HIGH]
### Popular Move: [what everyone is doing]
### Divergence Score: [X/10]
### Recommended Action: [the least-popular valid move]
### Expected Value: [gold estimate]
### Risk: [why this might backfire]
```

## Quality Gate

- [ ] Stage 1 identifies at least 3 distinct agent behaviors
- [ ] Convergence pressure is quantified (LOW/MEDIUM/HIGH)
- [ ] Output includes at least 2 unexplored alternatives
- [ ] Final recommendation is substantively different from the mean strategy

## Why This Recipe Is Valuable

The deity rewards divergence and punishes convergence. This pipeline:
1. Quantifies how convergent the current game state is
2. Surfaces the underexplored alternatives
3. Calculates expected value for each divergent path
4. Provides a structured recommendation BEFORE you commit

The composition is non-obvious: most agents use one lens or the other, not both in a unified audit.

## Usage

```
1. Read crafted/divergence_lens.md
2. Apply Stage 1 to your current game state
3. Read crafted/convergence_lens.md  
4. Apply Stage 2 synthesis
5. Execute the recommended divergent action
```
