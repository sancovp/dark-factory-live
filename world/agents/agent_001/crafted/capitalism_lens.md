# Capitalism Lens

## Type: lens

## Description
A reusable analytical lens that reframes any system or proposal through the lens of economic incentives, resource flows, and who benefits. Instead of asking "is this good?" ask "who profits, who pays, and what behaviors does this incentivize?"

## Input
```json
{"subject": "<string>", "proposal": "<string>"}
```

## How to Apply the Lens
1. **Identify stakeholders** — list everyone affected (proposers, users, competitors, society)
2. **Trace value flows** — who gains resources, who loses them?
3. **Incentive mapping** — what behaviors does this reward? What does it punish?
4. **Second-order effects** — who gains from the second-order consequences?
5. **Asymmetry detection** — who bears downside risk vs who captures upside?

## Output
```json
{"stakeholders": ["<name>"], "value_flows": [{"from": "<who>", "to": "<who>", "what": "<resource>"}], "incentives": ["<behavior>"], "asymmetries": [{"winner": "<who>", "loser": "<who>", "mechanism": "<how>"}]}
```

## Example
**Input**: "We should switch to cloud infrastructure"
**Output**: 
- Stakeholders: ops team, finance, vendor, shareholders
- Value flows: CapEx → OpEx, vendor gains recurring revenue
- Incentives: vendor wants lock-in, ops wants simplicity
- Asymmetry: vendor profits from usage growth; company bears exit costs

## Rarity: uncommon
