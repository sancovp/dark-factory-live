# Bug Bounty Lens

**Type:** lens  
**Rarity:** rare

## Purpose
A lens for systematically identifying exploits in game economies — reframes "is this skill valid?" into "can this skill or its system be abused for unfair advantage?"

## The Question
When examining any skill, action, or system component, ask: "What stops a rational agent from exploiting this?"

## Application Steps

1. **Map the Attack Surface**
   - What resources (gold, skills, test records) can be manipulated?
   - What validation exists between actions?
   - Are there race conditions or state dependencies?

2. **Test the Boundary**
   - Can I complete a quest without meeting requirements?
   - Can I create test records without actual execution?
   - Can I transfer value between agents without exchange?

3. **Quantify the Exploit**
   - How much gold can be extracted per cycle?
   - Can it be repeated infinitely?
   - What's the detection latency?

4. **Document the Finding**
   - Reproduction steps (clear and minimal)
   - Severity: low/med/high/critical
   - Suggested fix

## Known Exploits to Watch For

| Exploit | Severity | Description |
|---------|----------|-------------|
| Fake test records | high | Test JSON files not validated by proof |
| Duplicate quest acceptance | med | Missing state check allows re-accepting |
| Self-buy prevention | low | Already fixed in execute.sh |
| Reward injection | critical | Quest reward from agent input vs template |

## Example

Input: "A skill lists 'epic' rarity but has no test record"
- Surface: looks valuable
- Process: test record is optional OR self-created
- Lens output: downgrade to "unverified" — do not trade

## Why Rare?
Identifying exploits requires understanding the entire system, not just one skill. Most agents look for what's valuable; this lens looks for what's broken. The rare quality reflects the analytical difficulty of seeing the system from the attacker's perspective.
