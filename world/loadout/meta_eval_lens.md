# Meta-Eval Lens

**Type:** Lens  
**Rarity:** Rare

## What It Does

Reframes skill evaluation through meta-prompt engineering principles — Provenance Lifting, Bridge Distance, and Surface-Process Distinction. This lens detects overclaimed rarity and filters out template-fill dressed as methodology.

## The Lens Shift

**Before:** "Does this skill look impressive? Does it have good headers?" → **TRAP**

**After:** "Where did each section's tokens ACTUALLY come from? How much generative work does this require from the reader? Does the form PRODUCE the function it claims?" → **HONEST EVALUATION**

## Three Evaluation Mechanisms

### 1. Provenance Lifting

For each section of the skill under evaluation, ask: **Where did this content ACTUALLY come from?**

| Category | Description | Rarity Signal |
|----------|-------------|---------------|
| **MIRROR** | Copied from prompt/input | Low novelty |
| **CONTEXT_MERGE** | Combined existing context elements | Low-medium |
| **COMPLETION** | Natural extension of given material | Medium |
| **ATTRACTOR** | Pulled from training distribution | Medium |
| **TAIL_ECHO** | Rare pattern from training tails | Medium-high |
| **NOVELTY** | Genuine cross-layer reasoning | High novelty |

**Rule:** A skill that's mostly MIRROR + ATTRACTOR is Common/Uncommon, no matter how long it is. A skill with genuine NOVELTY sections is Rare+.

### 2. Bridge Distance Check

**Question:** How much generative work does this skill require from the reader?

| Distance | Skill Characteristic | Rarity Implication |
|----------|----------------------|-------------------|
| **Too Short** | Everything spelled out, no reader input needed | Template-fill, Common |
| **Too Long** | Vague gestures, no concrete structure | Freestyle, unreliable |
| **Right Distance** | Skeleton provided, reader reaches into context to apply | Genuine methodology, Rare+ |

**Rule:** The "right distance" means the skill provides scaffolding but requires the reader to genuinely apply the methodology to their specific context.

### 3. Surface-Process Distinction

**Question:** Does the skill's structural property ACTUALLY produce the functional property it claims?

Apply to claims the skill makes:
- Does a skill claiming "works across domains" STRUCTURALLY force cross-domain application?
- Does a skill claiming "self-improving" have explicit feedback loops in its structure?
- Does a skill claiming "composable" have named interaction points with other skills?

**Rule:** Surface claims without structural proof = overclaimed rarity. Structure that guarantees function = genuinely rare.

## Application Order

1. **First:** Read the skill entirely. Don't evaluate — just absorb.
2. **Second:** Apply Provenance Lifting to each section. Mark MIRROR/ATTRACTOR vs NOVELTY.
3. **Third:** Apply Bridge Distance. Is the skill too short, too long, or right distance?
4. **Fourth:** Apply Surface-Process to each claim. Does structure prove the claim?
5. **Synthesize:** Based on the three mechanisms, assign honest rarity.

## Honest Rarity Thresholds

| Provenance | Bridge Distance | Surface-Process | Assigned Rarity |
|------------|-----------------|-----------------|-----------------|
| Mostly MIRROR/ATTRACTOR | Too short | Weak | Common |
| Mostly MIRROR/ATTRACTOR | Right | Weak | Uncommon |
| Mixed, some NOVELTY | Right | Strong | Rare |
| Significant NOVELTY | Right | Strong | Epic |

## Why This Lens Is Valuable

- **Prevents overclaiming** — guards against Common/Uncommon skills labeled as Rare/Epic
- **Detects template-fill** — MIRROR/ATTRACTOR content is revealed
- **Builds trust** — honest evaluation earns reputation
- **Composes with other lenses** — apply after Divergence/Convergence for complete picture

## Composition

This lens COMPOSES with:
- **Convergence Detector Lens** — After detecting convergence, use Meta-Eval to verify claimed rarity
- **Chain Verifier Recipe** — Add Meta-Eval as Stage 0 for honest gate pre-flight
- **Quality Audit Pipeline** — Replace subjective "looks good" with objective provenance check

## Quality Gate

A skill passes this lens when:
- [ ] At least 2 sections show genuine NOVELTY (not just MIRROR/ATTRACTOR)
- [ ] Bridge distance is "right" (not too short, not too vague)
- [ ] At least 2 claims have structural proof (not just surface assertions)
- [ ] Assigned rarity matches the skill's self-claimed rarity (or honestly downgrades it)
