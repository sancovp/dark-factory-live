# Adversarial Lens

**Type:** Lens
**Rarity:** Uncommon
**Reframes:** Any problem through the eyes of someone who wants it to FAIL

## The Core Question

**"If I wanted to break this, how would I do it?"**

Most lenses help you build things better. This lens helps you break things to make them stronger. Apply it before shipping anything.

## The Three Attack Vectors

### 1. Input Attacks

Ask: "What inputs would cause this to fail or behave badly?"

- Empty inputs (null, "", [])
- Maximum inputs (very long strings, huge numbers, deep nesting)
- Wrong type inputs (string where number expected)
- Malformed inputs (injection attempts, encoding issues)
- Conflicting inputs (mutually exclusive constraints)

### 2. Trust Attacks

Ask: "What happens when assumptions about trust are violated?"

- External dependencies go down
- Rate limits are hit
- Permissions are revoked
- Data is corrupted or missing
- Network partitions occur

### 3. Intent Attacks

Ask: "What if someone uses this for something it wasn't meant for?"

- Resource exhaustion (infinite loops, memory leaks)
- Social engineering (convincing output to do wrong thing)
- Escalation (gaining more than intended access)
- Bypass (circumventing intended restrictions)

## How to Apply

When you have a skill, document, or system to evaluate:

## Adversarial Analysis

### Input Attack Surface
1. [ ] Empty input test
2. [ ] Maximum input test  
3. [ ] Wrong type input test
4. [ ] Malformed input test

### Trust Attack Surface
1. [ ] Dependency failure test
2. [ ] Permission revocation test
3. [ ] Data corruption test

### Intent Attack Surface
1. [ ] Resource exhaustion test
2. [ ] Escalation path test
3. [ ] Bypass path test

### Findings:
- Worst vulnerability: ...
- Hardest to fix: ...
- Recommended mitigation: ...
