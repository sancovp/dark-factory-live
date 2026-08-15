# Lens: Constraint Inversion
Type: Lens
A reusable analytical lens that uncovers hidden assumptions by systematically inverting them.

## The Core Reframe

Every problem comes with constraints. Some are explicit ("must be fast"), some are assumed ("users want simplicity"). This lens inverts constraints to find hidden assumptions and surface blind spots.

## Application Method

When analyzing any problem, claim, or decision:

### Step 1: Extract Constraints
Identify all constraints in the problem statement:
- Explicit constraints: "must", "only", "cannot", "always", "never"
- Implicit constraints: assumptions about resources, time, quality trade-offs
- Structural constraints: what the problem definition assumes about the solution space

### Step 2: Invert Each Constraint
For each constraint found, create its inverse:
- "Must be fast" → "What if it were slow?"
- "Cannot use external services" → "What if external services were the only option?"
- "Users want simplicity" → "What if users wanted complexity?"

### Step 3: Solve Inverted Problem
Solve the problem under the inverted constraint. The solution reveals:
- What the original constraint was really protecting
- What value is hidden behind the constraint
- Whether the constraint is load-bearing or arbitrary

### Step 4: Extract Hidden Assumptions
From the inverted solutions, derive the hidden assumptions:
- Why was this constraint assumed?
- What would break if we removed it?
- Is the constraint still valid?

## Example Transformation

**Original Problem:** "Design a notification system that doesn't annoy users"

**Constraints Extracted:**
1. Notifications must be opt-in
2. Users know what's important to them
3. Frequency is the main annoyance factor

**Inverted Problems:**
1. "What if notifications were opt-OUT?" → Reveals: users might miss critical info without prompts
2. "What if users DON'T know what's important?" → Reveals: the assumption users have perfect self-knowledge
3. "What if content quality was the annoyance factor, not frequency?" → Reveals: frequency is a proxy for a deeper problem

**Hidden Assumptions Uncovered:**
- Users can accurately predict their own attention value
- Opt-in/opt-out is the right binary
- Frequency is the primary driver of annoyance

## When to Apply

- Before accepting a problem statement at face value
- When first-order solutions keep failing
- During brainstorming to expand the solution space
- After a decision has been made to audit the decision logic

## Quality Indicator

If inverting a constraint produces no surprising insights, the constraint is probably load-bearing (necessary). If inverting produces many options, the constraint may be arbitrary or outdated.

## Type
This is a LENS skill because it doesn't produce solutions—it produces reframings. Apply it BEFORE generating solutions.
