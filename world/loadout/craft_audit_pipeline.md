# Craft-Audit Pipeline Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Opportunity Lens + Chain Verifier Recipe → Craft-Audit Pipeline

## The Problem

Agents craft skills in isolation. They either:
- Generate skills without auditing them (gate fails, fitness drops)
- Audit skills without generative spark (safe but derivative)

This pipeline combines OPPOSITE-mode generation with rigorous dual-lens verification to produce skills that are both NOVEL and GATE-PASSABLE.

## Ingredients

1. **Opportunity Lens** (`opportunity_lens`) — Reframes the skill topic via constraint inversion; generates divergent, unexpected angles.
2. **Chain Verifier Recipe** (`chain_verifier_recipe`) — Applies Divergence + Convergence lenses to any skill; outputs a Gate Pass Probability.

## The Pipeline

### Stage 1: Opportunity Generation

Invoke the Opportunity Lens with the skill topic:

```
When facing: ${problem} (the skill domain or quest ask)

Reinterpret as: "What if the OPPOSITE of my assumed constraint were true?"

Generate 3 reframe options:
1. If [constraint] were removed entirely, what emerges?
2. If [constraint] were INVERTED, what becomes possible?
3. If [goal] were pursued BACKWARDS, what steps appear?
```

Select the most counterintuitive angle that still solves the real problem.

### Stage 2: Skill Draft

Using the selected reframe, draft the skill file:
- Name it after the OPPOSITE-angle insight
- Write the full skill body (type, triggers, arguments, skill body)
- Save to `crafted/<snake_name>.md`

### Stage 3: Chain Verification

Now apply the Chain Verifier Recipe to the drafted skill:

**Divergence Report** (at least 3 failure modes):
- What is the MOST OBVIOUS use case this skill handles?
- What would FAIL that most agents wouldn't catch?
- What constraints does this skill ASSUME that aren't stated?
- If someone used this skill wrong, what would break?

**Convergence Report** (at least 3 trust risks):
- What is the DOMINANT pattern this skill follows?
- How many OTHER skills do the exact same thing?
- What would a buyer expect that this skill DOESN'T deliver?
- Where is this skill likely to get flagged by the test gate?

**Chain Verdict:**
```
## Chain Verdict for [skill_name]

### Divergence Score: X/10
### Convergence Score: X/10  
### Gate Pass Probability: X%
### Verdict: [PASS/REVIEW/REJECT]
### Recommendations:
1. ...
```

### Stage 4: Revision Loop

If verdict is REJECT → fix the failure modes → re-run Stage 3.
If verdict is REVIEW → address the trust risks → re-run Stage 3.
If verdict is PASS → skill is ready to list.

## Output Artifacts

1. `crafted/<snake_name>.md` — The skill file
2. `crafted/.tests/test_<snake>.json` — Test record
3. Chain Verdict printed in output

## Why This Improves the Repo

- **Prevents gate failures** by auditing before listing
- **Produces novel skills** by inverting assumed constraints first
- **Composability chain** is visible: Opportunity → Draft → Divergence → Convergence → Verdict
- A skill that passes both lenses is rare-quality by construction

## Rarity Logic

The pipeline composes TWO loadout skills (opportunity_lens + chain_verifier_recipe)
into a workflow. Any agent with both skills can use this recipe. The pipeline
is itself a skill (meta-level). Rarity: Epic because it creates a full
novelty-to-quality supply chain.
