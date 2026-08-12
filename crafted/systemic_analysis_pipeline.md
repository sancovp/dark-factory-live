# Recipe: Systemic Analysis Pipeline
Type: Recipe
Output Type: Epic

## What It Does
Composes Causation Lens + Second-Order Lens + Divergence Analyzer into a complete claim defense pipeline. Transforms surface-level observations into causally-sound, second-order-aware, self-defensive analyses.

## Ingredients (all required)
1. **Causation Lens** (Rare) — converts correlations into testable causal hypotheses
2. **Second-Order Lens** (Uncommon) — forces consideration of consequences of consequences
3. **Divergence Analyzer** (Rare) — provides adversarial failure mode framework

## Assembly Instructions

### Step 1: Surface Capture
Start with the raw claim or observation to analyze.
- Record exact statement as stated
- Identify what type of claim it is: causal, correlational, prescriptive, predictive

### Step 2: Causation Filter
Apply Causation Lens FIRST:
- "What causal mechanism could produce this?"
- "What changed to make this visible?"
- "What evidence would disprove this mechanism?"

If no mechanism exists, mark claim CORRELATIONAL ONLY and proceed to Step 4.

### Step 3: Second-Order Expansion
Apply Second-Order Lens to the causal hypothesis:
- Immediate Effect: What happens directly?
- First-Order Response: How do people/systems react?
- Second-Order Response: How do they react to those reactions?
- Equilibrium: Where does this stabilize?

If second-order analysis reverses first-order conclusion, mark accordingly.

### Step 4: Adversarial Defense
Apply Divergence Analyzer structure:
- "What input would make this analysis fail?"
- "What's the WORST conclusion this could support?"
- "Where does this assume something it shouldn't?"

Mark surviving claims: [DEFENDED]
Mark failing claims: [VULNERABLE → REVISE]

### Step 5: Synthesis
Produce final output with:
- Section: "Causal Mechanism" (from Step 2)
- Section: "Second-Order Trajectory" (from Step 3)
- Section: "Failure Modes Considered" (from Step 4)
- Section: "Defended Conclusions" (surviving claims only)
- Section: "Blind Spots" (honest acknowledgments)

## Quality Gates
- If causation filter marks CORRELATIONAL ONLY: can you still apply second-order? (Yes: pipeline still useful)
- If second-order reverses conclusion: did you acknowledge this reversal explicitly? (Required)
- If no claims survive adversarial defense: the original claim is unsound, report this)

## Expected Rarity
Three Rare ingredients + structured synthesis → Epic output
The composition creates value none of the parts achieve alone.

## Use Cases
- Evaluating proposed code changes before implementation
- Analyzing bug reports for root cause vs symptoms
- Assessing architectural decisions for long-term consequences
- Reviewing claims in documentation or PR descriptions
