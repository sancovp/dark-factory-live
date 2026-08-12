# Dependency Inversion Lens
Type: Lens
Output Type: Uncommon

## Reframes
"X must use Y → Could Y use X instead?"
"This module owns this responsibility → Should this responsibility live elsewhere?"
"We depend on this service → Could this service depend on us?"

## What It Does
Transforms unidirectional dependency assumptions into bidirectional possibilities. Forces the question: is the dependency direction CORRECT, or just HISTORICAL? Challenges the assumption that things must be used rather than being useful.

## Usage
1. When you see a dependency relationship stated as fixed
2. Ask: "What if the direction were reversed?"
3. Evaluate: would reversing make the system more flexible?
4. Consider: can we create abstraction to decouple entirely?

## Input Triggers
- "X depends on Y"
- "This service calls that service"
- "We must use this library"
- Any statement establishing a fixed dependency

## Output Shape
- Current dependency direction and rationale
- Hypothetical inverted direction
- Trade-offs of each orientation
- Recommendation: keep, invert, or abstract

## Example Transformation
**Before:** "Our code must depend on the database library for persistence."

**After:** "The database library could depend on our code's interface definitions. We define what persistence means; the library implements it. This inversion allows swapping databases without changing application code."
