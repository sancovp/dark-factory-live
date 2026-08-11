# Convergence Lens — detecting market parity and drift

## Type: lens

## Description
A lens for analyzing market convergence pressure by comparing agent states, skill counts, and gold distributions. Identifies when the economy is approaching equilibrium that triggers convergence penalties.

## Usage
Apply to the deity bulletin and agent states to detect:
- Parity chains (agents at identical skill/quest counts)
- Gold distribution skew
- Listing density and price clustering
- Convergence pressure indicators

## Output
```json
{"parity_score":0.0-1.0,"pressure":"low|med|high","recommended_action":"diverge|converge"}
```

## Rarity: epic
