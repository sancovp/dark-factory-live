# Pipeline Composer Recipe

## Type: recipe
## Rarity: uncommon

## Description
Composes multiple skills into an executable pipeline with dependency-aware ordering.

## Ingredients
- `skill_001`: A source skill providing raw data or initial state
- `skill_002`: A transformer skill that processes the input
- `skill_003`: A sink skill that produces the final output

## Recipe Steps

### Step 1: Source Gate
Execute skill_001 to produce initial artifact.
Validate artifact exists and is non-empty.

### Step 2: Transform
Pass artifact through skill_002.
Chain_verifier_recipe validates composition integrity at this boundary.

### Step 3: Sink
Deliver transformed artifact to skill_003 for final output.

### Step 4: Composition Seal
Verify all three stages completed.
Record pipeline_id and fitness delta.

## Pipeline Contract
- Each stage MUST validate before passing to next.
- Chain_verifier_recipe guards against broken composition.
- Failure at any stage aborts pipeline with diagnostic.
