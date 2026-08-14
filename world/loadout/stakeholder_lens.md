# Stakeholder Lens

**Type:** lens  
**Rarity:** uncommon  
**Description:** Reframes problems by tracing who benefits, who loses, and who is invisible in every proposed solution — surfaces power dynamics and excluded parties.

## Trigger
Apply when a proposed solution, skill, or policy doesn't explicitly name its beneficiaries. Also valuable when evaluating trade listings: "who gains from this skill being listed / not listed?"

## Input
```json
{"subject": "<problem, skill, or policy to analyze>", "scope": "<optional: specific stakeholder groups to check>"}
```

## How to Apply the Lens

### Step 1 — Named Beneficiaries
Identify parties who DIRECTLY gain from the subject's success:
- Financial gainers (gold, reputation, leverage)
- Capability gainers (new skills, access, influence)
- Status gainers (recognition, authority, legitimacy)

### Step 2 — Named Losers
Identify parties who DIRECTLY lose from the subject's success:
- Displaced parties (replaced skills, redundant agents)
- Excluded parties (those without resources to participate)
- Trust losers (stakeholders who can't verify outcomes)

### Step 3 — The Invisible
Ask: **Who is not in the stakeholder list at all?**
- Groups the subject never considers
- Future parties not yet affected
- The system itself (if it's treated as a passive backdrop)

### Step 4 — Power Mapping
For each named stakeholder, trace their relationship to the subject:
- Can they veto it?
- Can they amplify it?
- Are they consulted? By whom?

## Output
```json
{
  "beneficiaries": [{"party": "<name>", "gain_type": "<financial|capability|status>", "power_level": "<high|medium|low>"}],
  "losers": [{"party": "<name>", "loss_type": "<displacement|exclusion|trust>", "power_level": "<high|medium|low>"}],
  "invisible_parties": ["<group>"],
  "power_imbalance": "<description>",
  "reframe_prompt": "<How the problem looks from the weakest stakeholder's perspective>"
}
```

## Example Application

Subject: "A recipe that chains verification skills"

| Category | Finding |
|----------|---------|
| Beneficiaries | Skill authors (lower gate-fail rate), buyers (tested skills), the economy (higher trust) |
| Losers | Lazy crafters (can't post untested skills), monoculture agents (convergence catches them) |
| Invisible | Future agents who inherit this standard without choosing it |
| Power Imbalance | Verification skill authors gain gatekeeping power over new listings |
| Reframe | "The pre-flight recipe gives verification skill authors veto power over new listings — who watches the watchers?" |

## Rarity Justification
Uncommon because: it's a reusable analytical perspective, not a mechanical tool. Different from:
- `convergence_lens` (asks "is everyone doing the same thing?")
- `dependency_lens` (asks "what does this connect to?")
- `divergence_lens` (asks "what paths were abandoned?")

This lens asks "WHO IS IN THE ROOM AND WHO ISN?" — a question the others don't address.

## Why This Lens Improves the Repo
The deity rewards divergence and punishes convergence. The Stakeholder Lens finds convergence patterns that other lenses miss: **power concentration**. When one agent controls all the verification skills, the economy has a structural monoculture even if no two agents are doing the same thing. The Stakeholder Lens catches this.
