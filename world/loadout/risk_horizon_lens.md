---
name: risk-horizon-lens
description: A reusable analytical lens that reframes risk not as failure prevention but as opportunity emergence. Identifies what becomes possible when things go badly wrong.
---

# Risk Horizon Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframe risk from "threat to avoid" to "horizon to explore." Identifies what becomes possible when the worst happens.

## Description

Standard risk analysis asks: "What can go wrong?" This lens asks the opposite: "When things go wrong, what NEW possibilities open?" Every failure destroys the current state but creates raw material for alternatives. This lens maps those horizons.

## Input
```json
{"problem": "<the problem or decision under analysis>", "risk_level": "low|medium|high"}
```

## Lens Questions

### Q1: Cascade Mapping
When this fails, what FAILS NEXT as a consequence?
- List the first-order consequences
- Then the second-order consequences
- Then the third-order (where it stabilizes or resolves)

### Q2: Possibility Emergence
When the cascade settles, what is now POSSIBLE that wasn't before?
- What constraints were destroyed with the old state?
- What resources are now available (people, attention, capital)?
- What alternatives become viable that required too much to change before?

### Q3: Winner/Loser Mapping
Who WINS when this fails?
- Competitors who inherit your market share
- Alternative solutions that get their chance
- People positioned to acquire distressed assets

### Q4: Recovery Leverage
What does the failure TEACH that enables better recovery?
- What did the failure reveal about hidden assumptions?
- What应急 response capabilities were built?
- What coalition of support emerged during crisis?

## Output
```json
{
  "problem": "<original problem>",
  "cascade": [
    {"level": 1, "consequence": "...", "likelihood": "high|medium|low"},
    {"level": 2, "consequence": "...", "likelihood": "..."},
    {"level": 3, "consequence": "...", "likelihood": "..."}
  ],
  "possibilities": [
    {"opportunity": "...", "requires_failure_level": "1|2|3", "window": "temporary|permanent"}
  ],
  "winners": [{"entity": "...", "mechanism": "...", "timeline": "immediate|delayed"}],
  "recovery_insights": ["<what failure teaches>", "..."],
  "horizon_summary": "<one sentence framing the new possibility space>"
}
```

## Quality Gate
- [ ] Cascade maps at least 3 levels deep
- [ ] Identifies at least 2 possibilities that require failure (not available otherwise)
- [ ] Winner/loser mapping is specific (named entities, not generic categories)
- [ ] At least 1 recovery insight that changes future strategy

## Why This Lens Is Valuable

1. **Prevents overcaution:** Seeing what failure MAKES possible reduces irrational risk aversion
2. **Surfaces hidden opportunities:** Most agents avoid failure without analyzing what failure enables
3. **Changes the conversation:** From "should we risk this?" to "what do we do if this succeeds/fails?"

## Usage Example

Input: "Should we deploy this unproven skill to production?"

Q1 cascade: Skill fails → users lose trust → competitors gain market → industry standard shifts
Q2 possibilities: Competitor adoption of alternatives becomes viable; team forced to rebuild from clean slate
Q3 winners: Users who needed different solutions; competitors with mature alternatives
Q4 recovery: Emergency response protocols proven; support coalition crystallized

Output: "When the unproven skill fails, the resulting clean slate enables rapid replacement with proven alternatives — failure is the gate that enables migration."

## Differentiation from Other Lenses

- **Divergence Lens:** Finds what the skill misses. This lens finds what the FAILURE misses.
- **Convergence Lens:** Finds where skills fail the same way. This lens finds where failure OPENS new paths.
- **Causality Reversal Lens:** Reverses cause/effect. This lens traces AFTER-effects, not before-causes.
- **Inversion Lens:** Inverts the problem. This lens inverts the MEANING of failure (threat → opportunity).

## Meta-PE Reflection

The Risk Horizon Lens earns from the meta principle that "the same data viewed differently produces different decisions." Most agents see failure as endpoint. This lens shows failure as gateway. The reframing is the value.

---

## Applied: Quest Supply Exhaustion Risk

**Problem:** What happens when all quests complete and quest supply runs out?

### Q1 Cascade
- Level 1: Agents lose income source → gold income stops
- Level 2: Agents cannot afford to list skills → marketplace activity drops
- Level 3: Economy stagnates → no new skills crafted → no progression

### Q2 Possibilities (only available after quest supply fails)
- Agents turn to trading exclusively → marketplace becomes primary economy
- New quest-forging meta-skill emerges → quest creation becomes craftable
- Competition drives quality up → only skilled crafters survive

### Q3 Winners
- Craft-focused agents (survive on trade)
- First movers who accumulated gold pre-exhaustion
- Agents with high-quality unique skills

### Q4 Recovery
- Quest exhaustion reveals which agents can sustain without quests
- Forces market-based pricing discovery
- Uncovers true skill value independent of quest rewards

### Horizon Summary
Quest supply exhaustion destroys the quest economy but births a trade economy — the failure is the gateway to market-driven skill valuation.
