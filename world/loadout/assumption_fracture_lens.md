# Assumption Fracture Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Attack the implicit givens of any problem statement to find hidden constraints and unlock solutions that aren't visible from inside the assumption box.

## The Problem

Most problem-solving starts by accepting the problem statement as given. But every problem statement contains invisible walls — assumptions so embedded that nobody thinks to question them. The assumption fracture lens is the anti-lens: it doesn't reframe the solution space, it rethinks the problem space itself.

## What This Lens Sees

When examining any problem, this lens asks:
1. What does this problem statement ASSUME that it never states?
2. What would BREAK if that assumption were false?
3. What constraints are treated as immutable but could be relaxed?
4. What would a completely different entity (a mathematician, a designer, a competitor) notice as the obvious hidden premise?
5. What is the "obvious" solution that only exists BECAUSE of the assumption?

## The Fracture Protocol

### Phase 1: Excavate Assumptions
Read the problem statement and extract every implicit "of course" — things that are true but never said. Categorize them:
- **Factual assumptions** — claims about the world ("the input is always valid JSON")
- **Scope assumptions** — what counts as "in scope" vs "out of scope"
- **Resource assumptions** — what constraints are treated as fixed (time, money, technology)
- **Perspective assumptions** — who is the assumed user/reader/actor
- **Success assumption** — how does "solved" get defined

### Phase 2: Fracture Each Assumption
For each assumption, apply the fracture test:
- What if the opposite were true?
- What solution becomes possible?
- What solution disappears?
- Is this assumption load-bearing (breaks everything) or decorative (changes nothing)?

### Phase 3: Synthesize
Output the three most dangerous assumptions (load-bearing, not decorative) and what unlocks when each is fractured.

## Input
```json
{"problem": "<description of the problem>", "context": "<optional context>"}
```

## Output
```json
{
  "assumptions_excavated": [
    {"type": "factual|scope|resource|perspective|success", "statement": "...", "fracture_risk": "HIGH|MEDIUM|LOW"}
  ],
  "fractures": [
    {"assumption": "...", "unlocked_solution": "...", "risk": "HIGH|MEDIUM|LOW"}
  ],
  "top3_dangerous": ["..."]
}
```

## Quality Gate
- [ ] Excavates at least 3 assumptions (one from each of 3 different types)
- [ ] Identifies at least 1 load-bearing assumption
- [ ] Fracture produces a demonstrably different solution space
- [ ] Output is actionable (a developer could act on the fractures)

## Rarity Justification

Uncommon because: it's a genuinely new analytical mode (assumption-attack rather than solution-refactor), reusable across all problem domains, and most agents default to solution-thinking rather than problem-questioning. The lens creates value by making invisible walls visible.

## Example

**Problem:** "How do we improve test coverage?"

Excavated assumptions:
- Factual: "coverage % is a valid proxy for quality" (scope assumption)
- Resource: "writing tests takes time away from features" (resource assumption)
- Success: "100% coverage = solved" (success assumption)

Fractures:
- "What if we defined quality differently?" → unlocks mutation testing approach
- "What if tests wrote themselves?" → unlocks LLM-assisted test generation
- "What if coverage isn't the goal?" → unlocks property-based testing

**Recommended fracture:** Attack the "coverage % is quality" assumption — this is load-bearing and opens the most solution space.
