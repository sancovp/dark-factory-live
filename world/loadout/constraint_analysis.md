# Constraint Lens Analysis: patch-5 Quest/Loadout System

**Applied by:** agent_002  
**Lens used:** constraint_lens.md

---

## Stated Constraints

1. Quests live in `quests/` as `.md` files
2. Each quest has explicit `## Reward N gold` header
3. Only `lens` and `recipe` types currently have quests
4. Loadout skills are fixed at boot

## Assumed Constraints (Hidden Walls)

| # | Assumed Constraint | Evidence | What Breaks If Removed |
|---|-------------------|----------|------------------------|
| 1 | Rewards are static per quest type | Both quests have fixed rewards | Reward tiers could vary by quality/difficulty |
| 2 | Only two quest types exist | Only q_forge_lens + q_recipe_chain | Could have meta-quests, audit-quests, trade-quests |
| 3 | Loadout is static at boot | No conditional loadout logic | Could earn loadout slots via performance |
| 4 | Quests don't chain | Each quest is independent | Could have multi-step questlines |

## Freedom Surface

The system ASSUMES:
- Reward = f(quest_id), not f(quality_output)
- All skills start equal in loadout
- No progression system for unlockables

**What becomes possible:**
1. Conditional rewards: epic skill = 2x base reward
2. Earned loadout slots: complete 5 quests → unlock 6th slot
3. Meta-quests: "craft a quest" → rewards crafting of the skill it describes
4. Dependency chains: "complete q_forge_lens to unlock q_master_lens"

## Genuine Constraints (Cannot Violate)

1. Quest files must be valid markdown (game engine reads them)
2. Gold amounts must be positive integers
3. Loadout skills must be valid skill files

---

**Analysis complete.** Installed `constraint_lens.md` to loadout.
