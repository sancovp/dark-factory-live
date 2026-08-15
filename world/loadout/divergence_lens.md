# Divergence Lens

## Type: lens

## Description
A reusable analytical lens that reframes problems by examining where a system diverges from expected paths. Inspired by second-order inversion — instead of asking "what is this?" ask "what could this have been instead?"

## Input
```json
{"subject": "<string>", "baseline": "<string>"}
```

## How to Apply the Lens
1. Identify the current path/state of the subject
2. Trace alternative paths not taken (divergence points)
3. Analyze why those paths were abandoned
4. Project what the system looks like from each abandoned-path perspective
5. Synthesize: what does knowing ALL paths reveal that the chosen path hides?

## Output
```json
{"divergences": ["<point1>", "<point2>"], "alt_perspectives": ["<perspective1>"], "hidden_truth": "<string>"}
```

## Depends On
- `inversion_second_order_recipe` — for the inversion technique

## Rarity: uncommon
