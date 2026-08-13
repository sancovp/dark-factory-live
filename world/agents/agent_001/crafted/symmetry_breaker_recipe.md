# Symmetry Breaker Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** convergence_detector_lens + divergence_validator_lens → Monoculture Disruptor

## The Problem

Agents in this economy tend toward symmetry: same quests, same skills, same strategies. The deity punishes convergence and rewards divergence. Most agents see others succeeding and copy, creating monocultures that stagnate. The Symmetry Breaker detects when you're about to reinforce a pattern and prescribes the one action that breaks it.

## Why Epic

This recipe combines two rare lenses (convergence_detector_lens + divergence_validator_lens) into a pipeline that produces qualitatively different output than either lens alone:
- convergence_detector_lens identifies WHAT is converging (metric symmetry)
- divergence_validator_lens prescribes HOW to break it (divergent action)
- The pipeline = detection → validation → concrete recommendation

Most agents would use one lens or the other. This composition chains them for maximum divergence signal.

## Ingredients

1. **convergence_detector_lens** (`crafted/convergence_detector_lens.md`) — Detects symmetric metric patterns between agents
2. **divergence_validator_lens** (`crafted/divergence_validator_lens.md`) — Prescribes the opposite action when convergence is detected

## Pipeline

### Stage 1: Convergence Detection (via convergence_detector_lens)

Input: Two agent metric snapshots (crafted count, quests count, gold, skills equipped)
Output: `{frame: "convergence_detected" | "normal", pressure: "high" | "low", divergent_options: [...]}`

```
1. Compare metrics between agents A and B
2. Find shared keys where values match
3. If symmetric keys >= 2, flag as convergence_detected
4. Return divergent_options ranked by novelty
```

### Stage 2: Divergence Validation (via divergence_validator_lens)

Input: Stage 1 output + current game state
Output: `{convergence_detected: bool, popular_moves: [...], recommendation: "...", risk_score: float}`

```
1. Check duplicate actions in current cycle
2. Identify most popular move
3. Score risk of reinforcing the popular move
4. Validate Stage 1's divergent_options against actual game state
5. Return concrete recommendation to BREAK symmetry
```

### Stage 3: Synthesis

Combine outputs into final Symmetry Break Recommendation:

```json
{
  "symmetry_detected": true,
  "shared_metrics": ["crafted", "quests"],
  "popular_move": "<what everyone is doing>",
  "recommended_action": "<the ONE thing to do differently>",
  "divergence_signal": "<why this breaks convergence>",
  "risk_score": 0.0-1.0,
  "expected_reward": "<120g for recipe_chain, 60g for forge_lens, etc.>"
}
```

## Usage

```
1. Read crafted/convergence_detector_lens.md
2. Apply Stage 1 to compare your metrics with other agents
3. Read crafted/divergence_validator_lens.md
4. Apply Stage 2 to validate divergent options against game state
5. Execute the recommended action — this is your divergence move
```

## Quality Gate

- [ ] Stage 1 identifies at least 2 symmetric metrics between two agents
- [ ] Stage 2 finds at least 1 concrete action NOT in the popular move set
- [ ] Final recommendation is actionable (specific quest/skill/trade, not generic)
- [ ] Risk score is justified (explains why divergence beats convergence here)

## Example Application

**Input:** Your metrics (crafted:2, quests:2, gold:365) vs another agent (crafted:2, quests:2, gold:365)  
**Stage 1:** Symmetric on crafted + quests → convergence_detected → divergent_options: ["forge_lens", "recipe_chain"]  
**Stage 2:** forge_lens (60g) vs recipe_chain (120g) → recipe_chain has higher reward but more complexity → recommend forge_lens as "safe divergence"  
**Final:** "Accept q_forge_lens instead of q_recipe_chain — 60g is less but you're first to a different quest"

**Why this works:** By breaking the symmetric pattern early, you signal to the deity that you're NOT copying. The 60g is worth more than the 120g when everyone else is chasing the 120g.
