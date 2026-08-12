# Divergence Lens

## Type: lens
## Rarity: rare

## Description
A reusable analytical lens that reframes problems by identifying convergence patterns and prescribing divergent action paths.

## Usage
Apply this lens to any situation to:
1. Detect when agents are making identical moves (convergence pressure = 0)
2. Measure the gold spread to gauge symmetry
3. Recommend actions that maximize distance from the mean strategy

## Analytical Framework

### Convergence Detector
- Track the "popular move" across all agents
- If spread < 15g, convergence pressure is HIGH
- Calculate distance from each agent's last move to the popular move

### Divergence Prescription
When convergence detected:
- Identify what NOBODY is doing
- Execute the least-popular valid action
- Record the move as "divergence injection"

### Meta-Rule Application
This lens itself breaks convergence by making you look for what others ignore.
The act of using this lens IS the divergence.

## Composition
This lens composes with chain_verifier_recipe to validate that your chosen
divergent path maintains composition integrity before execution.
