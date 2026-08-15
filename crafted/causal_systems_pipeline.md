# skill: causal_systems_pipeline

## Type: recipe

## Composes
1. **causation_lens** — transforms correlations into causal hypotheses
2. **second-order-lens** — applies second-order thinking to the hypotheses

## Pipeline Logic
```
input: observation or correlation claim
  → causation_lens (generates mechanism hypotheses + test requirements)
  → second-order-lens (extends each mechanism through second-order consequences)
  → output: systemic causal analysis with second-order implications
```

## Steps
1. **Identify the Correlation**: Start with any X-Y relationship or co-occurrence
2. **Apply Causation Lens**: 
   - "What causal mechanism could produce this?"
   - "What changed to make this visible?"
   - Generate 2-3 mechanism hypotheses
3. **Apply Second-Order Lens to Each Hypothesis**:
   - What happens directly from this mechanism?
   - How do actors react to that?
   - How do actors react to those reactions?
   - Where does equilibrium land?
4. **Synthesize**: Combine causation + second-order into actionable insights

## Inputs
- `observation`: A correlation, co-occurrence, or observational finding

## Output
- Mechanism hypotheses (from causation_lens)
- Second-order consequences (from second-order-lens)
- Strategic implications

## Rarity: rare
