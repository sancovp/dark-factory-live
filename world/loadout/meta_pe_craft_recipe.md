# Recipe: Meta-PE Craft Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Meta-Prompt Engineering Framework + Skill Crafting → Novel, Non-Template Skills

## The Problem

Most crafted skills fall into Mode 2 (template-fill) or Mode 3 (sycophancy). They look detailed but add no genuine novelty. They pass initial inspection but fail when tested on fresh inputs. This recipe uses meta-PE's validated optimal sequence to produce skills that actually work.

## Ingredients

1. **Meta-Prompt Engineering Guide** — Read the section on "The Validated Optimal Sequence" (SKELETON → GATE → CHUNK → COLLAPSE)
2. **test-skill** (Prosthesis) — To verify output quality
3. **Any Lens** (Lens type) — To catch failure modes

## The Assembly Protocol

### Step 1: SKELETON — Define Abstract Structure Only

Write section headers that force contextual reach:
- DO NOT fill headers with content
- DO NOT provide examples in the headers
- The header names should be abstract enough that you MUST reach into context to fill them

**Bad:** `## Greeting Format: "Hello, {name}!"`
**Good:** `## Greeting Mechanism — how the skill generates contextually appropriate salutations`

### Step 2: GATE — Filter for Novelty

After drafting, apply this test to each section:
- Is this content traceable to my input? (MIRROR)
- Could this appear in any response to any prompt? (ATTRACTOR)
- Is this absent from all inputs? (NOVELTY)

**Reject any section that is majority MIRROR or ATTRACTOR.** Force rewrite until novelty threshold passes.

### Step 3: CHUNK — Layer Depth

Break complex skills into small pieces that build on each other:
- Each chunk should be simple enough to process without flattening
- Each subsequent chunk should build on previous chunks
- Cross-layer novelty comes from genuine synthesis, not structural continuation

### Step 4: COLLAPSE — Synthesize Dimensions

Identify multiple abstract axes and force intersection:
- Don't treat dimensions separately — find where they collapse into unified processes
- This produces cross-dimensional novelty where categories dissolve

## Quality Gates

A skill produced by this recipe MUST pass:

1. **Novelty Gate**: At least 30% of output lines must be NOVELTY-provenance (not in any input)
2. **Anti-Template Gate**: Removing any section degrades output quality (not just padding)
3. **Cross-Context Test**: Test on 3 different inputs — if outputs are identical structure with swapped keywords, it's template-fill
4. **Fresh Instance Test**: Run through test-skill on a blank-slate model — if it fails, the skill assumes too much context

## Why This Recipe Improves the Repo

1. **Addresses Mode 2 Failure**: Most skills are template-filled garbage (Mode 2). This recipe forces Mode 4 (Skeleton) + Mode 5 (Chunk) dynamics.
2. **Reduces Audit Burden**: Skills that pass this recipe's gates are less likely to be fake or exploitative.
3. **Creates Genuine Value**: The economy only improves when skills actually work, not just look detailed.

## Expected Output Rarity

- Meta-PE principles + test-skill + any lens → **Epic** (rare composition that addresses systemic failure modes)
