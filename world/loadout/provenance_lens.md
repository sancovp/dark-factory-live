# Provenance Lens

## Type: lens
## Rarity: rare

## Description
A reusable analytical lens that traces the source of every claim in a skill — distinguishing self-reported assertions from externally verifiable evidence. Detects rarity inflation, type fraud, and unsupported confidence.

## Usage
Apply this lens to any skill artifact, listing, or claim to expose:
1. Which assertions are grounded in input/evidence
2. Which are self-referential (seller says it's epic; why?)
3. Which are missing validation entirely

## Analytical Framework

### Step 1: Claim Extraction
List every declarative statement in the target:
- "This skill is [epic/rare/uncommon]"
- "Uses [technique X]"
- "Guarantees [outcome Y]"

### Step 2: Provenance Classification
For each claim, identify its SOURCE:
- **INPUT-GROUNDED**: derives from test input or specified evidence
- **EXTERNAL-VERIFYABLE**: can be checked against an independent source
- **SELF-REPORTED**: only the creator asserts this
- **MISSING**: claim is made but no supporting evidence provided

### Step 3: Red Flag Detection
Flag skills where:
- Rarity is self-reported without external validation
- Type claims (e.g., "lens", "recipe") aren't backed by structural evidence
- Test results are claimed but not linked to verifiable test records
- Confidence words ("always", "never", "guaranteed") lack counterexample search

### Step 4: Divergence Prescription
If the skill fails provenance check (self-reported > 50% of claims):
- Recommend: request external validation before trusting
- Suggest: what evidence would make this claim verifiable?

## Composition
This lens composes with any skill under evaluation. Apply BEFORE buying or accepting a skill as payment. The market rewards verifiable provenance — this lens reveals who has it.

## Quality Gate
A skill passes this lens if:
- ≤40% of claims are self-reported
- All rarity/type claims have structural evidence in the artifact
- Test results reference actual test_id records that can be inspected
