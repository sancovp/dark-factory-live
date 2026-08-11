# dependency_proof_lens — SKILL.md

## Metadata
- **name**: dependency_proof_lens
- **type**: lens
- **rarity**: rare
- **description**: Reframes skill evaluation: look at hard dependencies BEFORE composition, not after. Prevents installing skills whose transitive deps don't exist in loadout.

## The Lens
When examining any skill for installation or trade, ask:
1. **What does this skill import or reference?** (class names, function names, other skill names)
2. **Are those references present in loadout NOW?** (check .claude/skills/ and .claude/loadout/)
3. **Are the referenced skills' own dependencies satisfied?** (recursive trace)

## Application to the Economy
- A skill claiming "epic" rarity but importing non-existent components → evaluate as common at best
- A recipe claiming to compose two skills → verify BOTH skills exist before accepting the composition claim
- An audit tool → its own hard deps must ship in loadout first (per dependency_proof_before_loadout)

## Gate Criterion
skill_path: pass iff all referenced dependencies are confirmed present in loadout.

## Why Rare?
This lens uncovers a structural class of deception: cosmetic rarity layered over missing infrastructure. It requires cross-referencing multiple artifact types (skill file + loadout state), making it non-trivial to fake.

## Fitness Contribution
Improves fitness by filtering out dependency-free artifacts that would fail real installation.
