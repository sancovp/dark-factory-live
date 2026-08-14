# Threat Model Lens

## Type: lens

## Description
A reusable analytical lens that reframes any problem by asking "how could this be exploited, broken, or fail?" Shift from building to attacking mindset — identify vulnerabilities, failure modes, and attack surfaces before they manifest.

## When to Use
- After designing a solution, before implementing it
- When auditing code for security vulnerabilities
- When evaluating third-party components or dependencies
- When diagnosing why a system broke — look backward through this lens
- Before accepting a skill claim (verify it cannot be gamed)

## How It Works

### Step 1: Enumerate Attack Surfaces
For the target system/problem, identify entry points:
- Input vectors (user input, API calls, file uploads)
- Trust boundaries (what do you assume is safe?)
- Dependencies (what third-party code do you rely on?)
- State transitions (where can things go wrong?)

### Step 2: Enumerate Failure Modes
Ask: "What could go wrong at each surface?"
- Injection attacks (SQL, command, prompt)
- Resource exhaustion (DoS, memory leak)
- Authentication/authorization bypass
- Data leakage or corruption
- Trust assumption violations

### Step 3: Prioritize by Impact
Rate each threat:
- Severity (1-5): How bad if it happens?
- Likelihood (1-5): How probable?
- Priority = Severity × Likelihood

### Step 4: Design Mitigations
For high-priority threats, design countermeasures:
- Input validation
- Boundary checks
- Rate limiting
- Audit trails

## Output
Threat Model with:
1. Attack surface inventory (numbered list)
2. Failure mode catalog with priority scores
3. Mitigation plan for top threats

## Example Application
Problem: A trade_post skill listing claims "epic" rarity

Surface: Rarity claims are self-assigned, not verified
Failure: An agent could claim any rarity without proof
Priority: HIGH — affects economy integrity
Mitigation: Request test_id, verify test record, cross-check with independent auditor

## Tags
- security
- audit
- adversarial-thinking
- vulnerability-analysis
- failure-mode
