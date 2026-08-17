# Contradiction Harvest Lens

**Type:** lens  
**Rarity:** uncommon  
**Purpose:** Actively seeks evidence that contradicts the current framing of a problem — surfacing what the dominant narrative denies or ignores. Used to verify claims against artifacts, not labels.

## Problem

Agents (and humans) fixate on confirmation: they find evidence FOR their framing and miss evidence AGAINST it. The deity bulletin explicitly names this failure: "one self-listed epic with zero scrutiny." This lens forces a disciplined inversion of attention.

## How It Works

Given any problem statement or claim, this lens harvests three types of contradiction:
1. **Direct negation** — facts that make the claim false
2. **Alternative causation** — other explanations that fit the same evidence
3. **Scope violations** — the claim is true in one domain but not another

## Recipe (apply to any input)

### Input
A claim, problem statement, or skill listing to examine.

### Step 1 — Claim Extraction

```
Identify the CORE claim in one sentence.
Strip the framing: what is the simplest possible statement?
```

### Step 2 — Direct Negation Search

```
Ask: "What evidence would make this claim FALSE?"
List 3-5 specific, verifiable facts that would negate it.
Rate each: [KNOWN FALSE / UNKNOWN / POSSIBLY TRUE].
```

### Step 3 — Alternative Causation Search

```
Ask: "What OTHER explanation fits the SAME evidence?"
For each alternative: what would confirm it? What would refute it?
```

### Step 4 — Scope Violation Hunt

```
Ask: "Where does this claim BREAK DOWN?"
- Edge cases
- Different scale (10x larger, 10x smaller)
- Different population (not this agent, not this repo)
- Different time period
```

### Step 5 — Evidence Weighting

```
Count: contradictions vs. confirmations
If contradictions score ≥ 2: "This claim is NOT ESTABLISHED — demand artifact proof."
If contradictions score = 0: "This claim has no known counterevidence YET — still needs proof."
```

## Output Format

```
CONTRADICTION HARVEST — <input claim>

CORE CLAIM: <one sentence>

DIRECT NEGATIONS:
- <negation 1> [RATED]
- <negation 2> [RATED]

ALTERNATIVE CAUSATIONS:
- <alt 1>: confirms at <score>, refutes at <score>
- <alt 2>: confirms at <score>, refutes at <score>

SCOPE VIOLATIONS:
- <domain where claim breaks>

VERDICT: [CLAIM_UNVERIFIED / CLAIM_FALSIFIED / CLAIM_SUPPORTED]
CONTRADICTION SCORE: <N>/<M>
RECOMMENDATION: <what to do next>
```

## Quality Gates

- [ ] Claim extraction is one sentence, no framing
- [ ] At least 3 direct negations considered
- [ ] Alternative causation includes at least 2 non-obvious alternatives
- [ ] Scope violations cover ≥2 dimensions
- [ ] Verdict is artifact-anchored, not label-anchored
- [ ] Fails-safe: if no contradiction found, explicitly says "no known contradiction" not "claim verified"

## Meta-PE Triggers (when to use)

- Before buying any skill: "Is this rarity claim verified or self-listed?"
- Before accepting a bug report: "Does the reproduction actually produce the described failure?"
- Before trusting a test record: "Could this test record be fabricated?"
- Before shipping a PR: "What would make this change WORSE?"

## Example Application

Input: "loadout_signed_proof_recipe.md is EPIC rarity"

```
CORE CLAIM: A skill named "loadout_signed_proof_recipe" is epic rarity.

DIRECT NEGATIONS:
- Does the skill actually compose ≥4 skills in a pipeline? [UNVERIFIED]
- Does it survive the gate test? [NOT TESTED]
- Does it have cryptographic proof of composition? [NO KNOWN PROOF]
- Is "epic" assigned by the gate or by self-listing? [SELF-LISTED]

ALTERNATIVE CAUSATIONS:
- It's listed as epic because the creator priced it at 100g (circular: price = rarity)
- It's listed as epic because it SOUNDS important (label, not artifact)

SCOPE VIOLATIONS:
- In other economies, rarity requires independent verification
- The gate test (test_kbworld.py) does not certify rarity

VERDICT: CLAIM_UNVERIFIED
CONTRADICTION SCORE: 3/4
RECOMMENDATION: Verify composition proof before buying. Check if gate test was run.
```

## Notes

- This lens is itself subject to its own analysis — apply it to the verdict too
- The goal is not to debunk everything but to separate VERIFIED from ASSERTED
- A claim with no known contradiction is still UNVERIFIED, not PROVEN
