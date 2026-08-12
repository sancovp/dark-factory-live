# Pattern Collapse Lens
Type: Lens

## Reframes
"Identical moves → What selection pressure is this convergence about to trigger?"
"Safe consensus → What fragility is hiding in the shared assumption?"

## What It Does
Detects when a population of agents (or strategies) becomes dangerously similar, signaling imminent selection pressure. Identifies the invisible collapse point before it manifests. Reframes "everyone is doing X" from "X is safe" to "X is about to be selected against."

## The Three-Stage Collapse Model
1. **Convergence** — agents discover the same dominant strategy independently
2. **Compression** — environment tightens around the convergent strategy's assumptions
3. **Selection Event** — a perturbation exploits the gap no one filled

## Usage
1. Survey what moves are being made by multiple agents
2. Identify the dominant pattern (mode of the move distribution)
3. Ask: "What does this shared assumption hide?"
4. Find the gap — the move no one is making
5. That gap is the divergence opportunity

## Input Triggers
- "Everyone is doing X" — applies the collapse model
- "This strategy is safe" — probes for hidden fragility
- "We're all in the same situation" — checks for compression pressure
- Near-identical agent stats — convergence pressure detected

## Output Shape
- The dominant pattern identified
- The hidden fragility (what the consensus ignores)
- The divergence prescription (what move is NOT being made)
- Estimated time-to-selection-pressure (short/medium/long)

## Example Transformation
**Before Pattern Collapse Lens:**
"Two agents, same gold, same skills_crafted, same quests. Mild pressure."

**After Pattern Collapse Lens:**
"Two agents making identical moves will trigger a selection event. Neither has filed a NEW skill this round. The gap: neither is creating novel artifacts. The divergent move: be the one who makes what the other is NOT making. Estimated pressure: immediate — the next round."
