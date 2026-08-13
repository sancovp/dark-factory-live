# Recipe: Convergence Through Divergence Pipeline
Type: Recipe
Output Type: Towering (Rare)
Yield: 1 full-cycle analytical pipeline that finds convergence by first exploring all divergences

## Ingredients
1. Recipe: Divergence Analyzer (Rare) — my defensive analysis pipeline
2. Lens: Second-Order Thinking (Common+) — sees consequences of consequences

## Assembly
1. **Start with your problem** (claim, decision, or question to resolve)
2. **Phase 1 - Divergence Exploration** (using Divergence Analyzer):
   - Apply adversarial lens to identify all failure modes
   - Use analysis template to structure each divergent path
   - Track provenance of each claim's evidence
   - Mark each claim as [DEFENDED], [VULNERABLE], or [GROUNDED]
3. **Phase 2 - Second-Order Convergence** (applying Second-Order Lens to defended paths):
   - For each [DEFENDED] + [GROUNDED] claim, ask:
     - "What happens when this is implemented?"
     - "How do people/systems react to that?"
     - "How do they react to those reactions?"
   - For each [VULNERABLE] claim, ask:
     - "If this fails, what second-order effects cascade?"
4. **Phase 3 - Convergence Synthesis**:
   - Find claims where first-order AND second-order effects align
   - These are your CONVERGENCE POINTS
   - Find claims where first-order is strong but second-order is weak
   - These need mitigation before proceeding
5. **Output**: 
   - Section: "Divergence Map" (from Phase 1)
   - Section: "Second-Order Analysis" (from Phase 2)
   - Section: "Convergence Points" (where all orders agree)
   - Section: "Remaining Risks" (second-order weaknesses)

## Quality Check
- Remove Divergence Analyzer. Can you find convergence without exploring divergences first? (Must: no → divergence phase is essential)
- Remove Second-Order Lens. Do convergence points hold under shallow analysis? (Must: no → second-order phase is essential)
- Remove both. Is surface analysis sufficient for this problem? (Must: no → combination creates non-obvious value)

## Expected Rarity
- Rare recipe + Common lens → Epic output
- The combination transforms defensive analysis into proactive convergence-finding

## Why This Recipe Works
Convergence found without divergence exploration is fragile. Convergence found through exhaustive divergence is robust. By applying second-order thinking only to defended, grounded claims, you avoid analysis paralysis while maintaining rigor.
