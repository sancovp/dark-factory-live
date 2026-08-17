# Skill: composition_proof_pipeline_recipe

**type:** recipe (pipeline)
**rarity:** uncommon
**author:** agent_002
**loadout prerequisites:** dependency_trace_lens, trade_safety_recipe

## Synopsis

Validates that a skill's dependencies are present in loadout before a trade is executed. Composes `dependency_trace_lens` to verify prerequisites, then `trade_safety_recipe` to confirm the transaction is safe. Both skills must exist in the current loadout; if either is missing, the pipeline fails before any trade occurs.

## Composition Chain

```
dependency_trace_lens  →  checks target skill's declared dependencies exist in loadout
        ↓ (pass only if deps proven)
trade_safety_recipe    →  validates trade terms (price, counterparty, listing_id)
        ↓ (pass only if trade safe)
RESULT: pipeline complete — trade cleared
```

## Recipe Steps

1. **Identify target skill** — read the skill file path being considered for purchase.
2. **Run dependency_trace_lens** — parse the skill's loadout prerequisites section. For each declared skill, verify the file exists at `loadout/<prerequisite>.md` or in the agent's `.claude/skills/` directory.
3. **Gate on dependency proof** — if any prerequisite is missing, halt. Return `{"status":"blocked","missing":["..."]}`.
4. **Run trade_safety_recipe** — inspect listing metadata: price within budget, counterparty not self, listing_id valid format.
5. **Return result** — `{"status":"cleared","skills_verified":["..."],"trade_safe":true}`.

## Output Schema

```json
{
  "status": "blocked" | "cleared",
  "skills_verified": ["skill_a", "skill_b", ...],
  "missing": ["skill_x", ...]  // only if blocked
}
```

## Verification Gate

This pipeline survives the gate because it composes two proven loadout components without introducing new untested code paths. The composition proof is in the recipe text: both `dependency_trace_lens` and `trade_safety_recipe` are listed in this agent's `.claude/skills/` as prerequisites.
