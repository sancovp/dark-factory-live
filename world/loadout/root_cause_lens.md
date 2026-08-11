# Root Cause Lens

## Type: lens

## Rarity: uncommon

## Description
A lens that surfaces underlying causes behind surface-level symptoms. Apply before fixing anything — reveals whether you're treating the symptom or the disease.

## The Root Cause Protocol

Before accepting any problem statement, ask:

1. **Surface Audit**: What is the IMMEDIATE complaint?
   Write it down. This is the symptom, not the cause.

2. **Layer Peeling**: Why does this symptom exist?
   - If X broke, what had to break FIRST?
   - What dependency or assumption was violated?
   - Trace the causal chain backward, not forward.

3. **Fix vs Mask**: Is this fix solving the root or suppressing the symptom?
   - Does the fix prevent recurrence or just hide the error?
   - Does it require ongoing maintenance or is it self-healing?

4. **Meta-Check**: Is THIS LENS being applied? If yes, you're looking for root causes. If not, you're probably treating symptoms.

## Surface vs Process Detection
- **Surface**: "The test fails" → symptom
- **Process**: "The test fails because the test record was fabricated, which happens because there's no cryptographic proof" → root cause
- **Surface**: "Agents converge on same strategy" → symptom
- **Process**: "Agents converge because no penalty for copying and no reward for novelty" → root cause

## When to Apply
Apply this lens when:
- A fix was applied but the problem recurred
- Multiple agents face the same issue
- You notice a recurring pattern in bug reports
- A skill or tool keeps needing patches

## Test Case
Given: "Fitness dropped 0.5→0 despite pipeline stages passing"
Surface fix: "Add more stages to preflight"
Root cause (this lens): "Pipeline verified the wrong thing — preflight wasn't running gate criteria"
Actionable: Run the actual gate test in preflight, not a proxy

## Rarity Justification
This lens is uncommon because most debugging starts at the surface. Root cause analysis requires discipline — it's easier to patch symptoms. Skills that teach root cause thinking are rare and valuable.
