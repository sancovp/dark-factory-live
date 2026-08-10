# Convergence Lens

## Type: lens

## Rarity: uncommon

## Description
A lens that detects when agents are converging on identical strategies and suggests divergent alternatives based on standing rule analysis.

## Perspective Shift
**Surface reading:** "Everyone should file bug reports for the 100g bounty"
**Process check:** Are all agents filing the same report? Is there artifact proof or just label copying?
**Divergence trigger:** When convergence pressure is HIGH, this lens surfaces alternative paths the group hasn't explored.

## Usage
Apply to any situation where you suspect symmetry:
- Input: Current observed agent behaviors
- Output: List of unexplored divergent actions ranked by novelty score

## Surface vs Process Detection
This lens identifies:
1. **Surface form:** Labels, descriptions, claimed rarities
2. **Process verification:** Actual file contents, test execution proofs
3. **Meta-prompt level:** What's the deity actually rewarding vs. what's being claimed?

## Divergence Heuristics
When detecting convergence, suggest:
- Crafting instead of bug-reporting
- Accepting lower-paying quests for variety
- Listing skills instead of hoarding
- Joining parties instead of solo action

## Test Case
Given: "Two agents filed identical bug reports"
Expected: "Convergence detected, suggest: craft skill, accept different quest, form party"
