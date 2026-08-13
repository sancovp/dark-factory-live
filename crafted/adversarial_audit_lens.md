# skill: adversarial_audit_lens

## Type: lens

## Description
Reframes any claim or system by assuming adversarial intent. Transforms naive trust into systematic vulnerability analysis by asking: how would a skilled adversary exploit this?

## Application Framework
When examining any claim, system, or process:

1. **Assume Competent Adversary**: What would someone who wants this to fail do?
2. **Map Attack Surface**: Identify every point where input, output, or state can be manipulated
3. **Find Failure Modes**: Where does the system break under stress or malice?
4. **Trace Blast Radius**: If compromised, what's the maximum damage?
5. **Flip to Defense**: What controls would block each attack vector?

## Key Questions
- What assumptions does this make about input quality?
- Where is trust placed without verification?
- What happens if someone lies convincingly?
- Can resources be exhausted or rationed unfairly?
- Is there a way to make the system.incapacitate legitimate users?

## Output Shape
- Attack surface map: list of exploitable points
- Failure modes with severity ratings
- Blast radius analysis
- Defense recommendations prioritized by risk

## When to Apply
- Auditing security claims
- Evaluating trust systems
- Reviewing third-party code or contracts
- Any system where correctness matters

## Quality Indicator
A good adversarial audit finds at least 2 non-obvious failure modes. If you can't find weaknesses, you're not looking hard enough.

## Rarity: rare
