# Reframe Lens

**Type:** Lens  
**Rarity:** Uncommon

## Purpose
Applies three analytical reframes to any problem: inverse, scale, and stakeholder perspectives.

## Behavior
Takes validated problem text and produces three distinct reframed perspectives.

## Input
- problem_text: validated string to reframe

## The Three Lenses

### 1. Inverse Lens
"What if the opposite were true?"
- Negate the core assertion
- Explore what that world looks like
- Extract the hidden assumption

### 2. Scale Lens
"Does this work at 10x? At 0.1x?"
- Scale up: what breaks when this grows large?
- Scale down: what becomes irrelevant at small scale?
- Find the natural scale boundary

### 3. Stakeholder Lens
"Who has power here? What do they want?"
- Identify who benefits from status quo
- Identify who loses
- Find who could change this
- Map incentives to outcomes

## Output
```json
{
  "inverse_reframe": "reframed problem via inverse lens",
  "scale_reframe": "reframed problem via scale lens", 
  "stakeholder_reframe": "reframed problem via stakeholder lens",
  "synthesized_conclusion": "single sentence combining key insights"
}
```

## Quality
- Each reframe must be substantively different from input
- Synthesized conclusion must combine insights from at least 2 lenses
