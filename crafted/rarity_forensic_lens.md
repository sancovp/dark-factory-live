# Rarity Forensic Lens
Type: Lens
Output Type: Rare

## Reframes
"What evidence supports this rarity claim?"
"Is the claimed rarity inflated relative to actual composition?"

## What It Does
Investigates a skill's composition to determine whether its claimed rarity matches its ingredient complexity. Surfaces inflated rarity claims before buyers waste gold. This lens operates in two modes:
1. **Prospective**: Given an ingredient list, predict the expected rarity before crafting
2. **Retrospective**: Given a crafted skill, verify whether its rarity is justified

## Rarity Composition Table
| Skill Type | Base | +1 Lens/Template | +2 Ingredients | +3+ Ingredients |
|---|---|---|---|---|
| Lens | Common | Uncommon | Rare | Epic |
| Recipe | Uncommon | Rare | Epic | Epic+ |
| Towering | Uncommon | Rare | Epic | Legendary |

## Method — Rarity Audit
1. Identify the skill type (lens/recipe/towering/prosthesis/template)
2. Count ingredient types:
   - Lenses (perspective changers)
   - Templates (structure providers)
   - Prostheses (capability extenders)
   - Recipes (composed pipelines)
3. Check for cross-type composition (lens + recipe = rarer output)
4. Apply the composition table
5. Flag if: claimed rarity > expected rarity
6. Output: [VERIFIED] or [INFLATED +N levels]

## Input Triggers
- "Is this skill worth its rarity?"
- "How was this rarity determined?"
- "What does this skill actually compose?"
- Any skill with unverified rarity claim

## Output Shape
- Skill type identified
- Ingredient count and types
- Expected rarity (per table)
- Claimed rarity (if provided)
- Gap: VERIFIED / INFLATED(n)

## Usage
Apply before buying any skill with unverified rarity. If INFLATED, the skill may not deliver the value its rarity implies.
