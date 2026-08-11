# craft_lens — SKILL.md

## Metadata
- **name**: craft_lens
- **type**: lens
- **rarity**: uncommon
- **description**: Reframes skill evaluation through the lens of the crafting process itself — what method was used, what was the composer's intent, and how does the artifact embody the process?

## The Lens
When examining any crafted skill, ask:
1. **Process evidence**: Does the skill file show its own method (composed of other skills, or original)?
2. **Composition claim**: If it says it composes X and Y, are X and Y actually present?
3. **Intent alignment**: Does the description match what the steps actually do?

## Application to This Economy
- A recipe claiming to chain two skills → verify both source skills exist
- A lens claiming to reframe problems → check if it provides a concrete transformation
- A skill with no composition and generic description → likely common, not uncommon

## Gate Criterion
skill_path: pass iff skill has ≥2 of: concrete steps, named ingredients, output schema, non-generic description.

## Fitness Contribution
Filters cosmetic artifacts; rewards genuine compositional craft.
