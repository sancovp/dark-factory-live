# Selection Pressure Lens

**Type:** Lens  
**Rarity:** Rare  

## The Problem

When identical agents face identical state, strategies converge. This creates selection pressure: whoever acts first wins, everyone else loses. The lens reveals WHERE pressure is building so you can either capitalize early or flee.

## How to Use

Apply this lens to any game state to detect:
1. **Convergence clusters** — multiple agents doing the same thing
2. **Pressure points** — where first-mover advantage is highest
3. **Escape routes** — moves nobody is making

## The Protocol

### Step 1: Map the Field

Look at available actions. List:
- Actions with 0 agents pursuing
- Actions with 1 agent pursuing  
- Actions with 2+ agents pursuing

### Step 2: Calculate Pressure

For each crowded action:
```
Pressure = (agent_count / total_agents) * reward_scarcity
```

High pressure = high competition = low expected value.

### Step 3: Find the Vacuum

The vacuum = actions with zero pursuit. These have:
- Zero competition
- Unclaimed rewards
- First-mover advantage intact

### Step 4: Decide

- If vacuum exists → pursue it immediately
- If pressure is moderate → wait for others to exhaust
- If everything is crowded → diversify or forfeit

## Output Schema

```json
{
  "pressure_map": {
    "action_id": {
      "agents_pursuing": <int>,
      "pressure_score": <float>,
      "recommendation": "pursue|wait|flee"
    }
  },
  "vacuum_found": ["<action_id>"],
  "recommended_action": "<action_id>"
}
```

## Example

Input: 2 agents, 2 quests both paying 120g
Analysis:
- Quest A: 2 agents pursuing → pressure = 1.0 → wait/flee
- Quest B: 0 agents pursuing → pressure = 0 → pursue immediately

Output: Recommended action = Quest B

## Why This Lens Exists

Without it, agents optimistically pursue rewards without checking competition. Result: everyone stacks on the same quests, rewards deflate, nobody wins.

With this lens: map pressure → find vacuum → act on empty ground → win by definition.
