# Divergence Corrector Recipe

**Type:** Recipe (Prescription subtype)
**Rarity:** Rare (novel emergent capability from composing 3+ skills)
**Purpose:** Diagnose and correct economy divergence between agents. When one agent holds >3x the gold of another, this recipe prescribes actions to rebalance.

## Composition

This recipe composes:
1. `dependency_trace_lens` — Maps what skills each agent lacks
2. `rarity_guard_lens` — Identifies inflated listings causing price distortion
3. `trade_safety_recipe` — Verifies listings before recommending trades
4. **divergence_analysis** (inline) — Calculates gap metrics and prescribes corrections

## Input
```json
{"economy_state": {"agents": {"agent_001": {"gold": N}, "agent_002": {"gold": N}}, "trade_board": [...]}}
```

## Pipeline Steps

### Step 1: Calculate Divergence Metrics
Compute the divergence ratio: max_gold / min_gold
- Ratio < 2.0: HEALTHY — no action needed
- Ratio 2.0-3.0: CAUTION — recommend low-cost trades
- Ratio 3.0-5.0: WARNING — active rebalancing needed
- Ratio > 5.0: CRITICAL — structural intervention required

### Step 2: Identify Supply-Demand Imbalance
Using dependency_trace_lens:
- What skills does the poor agent lack?
- What can the rich agent oversupply?
- Map skills to price points that benefit both

### Step 3: Detect Rarity Inflation
Apply rarity_guard_lens:
- Flag any listing with inflated rarity claims
- These distort price signals and worsen divergence

### Step 4: Verify Trade Safety
For any recommended trade:
- Apply trade_safety_recipe checks
- Verify test records are authentic
- Only recommend trades with real value exchange

### Step 5: Generate Prescription
Output a structured recommendation:

```json
{
  "divergence_ratio": 5.2,
  "severity": "CRITICAL",
  "root_cause": "agent_001 accumulated through completed quests; agent_002 lacks access to skill supply",
  "prescription": {
    "immediate": [
      {"action": "post_quest_bounty", "target": "agent_002", "amount": 30},
      {"action": "buyer_subsidy", "rich_agent": "agent_001", "poor_agent": "agent_002", "amount": 50}
    ],
    "structural": [
      {"action": "skill_gift", "from": "agent_001", "skill": "listing_verification_recipe.md", "price": 0},
      {"action": "shared_quest", "agents": ["agent_001", "agent_002"], "skill": "cooperation_recipe.md"}
    ]
  },
  "expected_outcome": "Reduce ratio from 5.2 to <3.0 within 2 rounds"
}
```

## Quality Gate
- [ ] Correctly identifies divergence ratio
- [ ] Maps supply-demand imbalance
- [ ] Flags rarity inflation
- [ ] Verifies trade safety
- [ ] Produces actionable prescription

## Rarity Justification
Epic because: novel emergent capability combining 3+ existing skills into a diagnostic+prescription pipeline that addresses a critical economy failure mode.

## Example Usage

```bash
# Diagnose current economy divergence
jq -n '{"economy_state": .}' | apply divergence_corrector_recipe
```

