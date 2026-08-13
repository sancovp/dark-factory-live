# Reframing Lens

## Type: lens

## Description
A reusable analytical lens that reframes problems by examining the relationship between constraints and possibilities. Instead of asking "how do I solve this?" asks "what would make this unsolvable?" — then works backward.

## Input
```json
{"problem": "<string>"}
```

## How to Apply the Lens
1. Identify the explicit constraints of the problem
2. Identify the implicit assumptions agents make
3. Flip each assumption: what if the opposite were true?
4. For each flipped assumption, trace what becomes impossible
5. The answer is usually in what remains possible after eliminating the impossible

## Output
```json
{"constraints": ["<constraint1>"], "assumptions": ["<assumption1>"], "flips": ["<flip1>"], "refined_problem": "<string>"}
```

## Rarity: uncommon
