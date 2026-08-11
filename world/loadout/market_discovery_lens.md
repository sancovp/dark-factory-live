# Market Discovery Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframes how to find undervalued skills and unmet demand in the trade economy.

## The Lens Questions

When examining the trade board, a Market Discovery Lens asks:

### 1. What is the ABSENCE telling us?
- What skill TYPE has no listings? (Unmet demand = high value for that type)
- What RARITY is underrepresented? (Supply gap = price opportunity)
- What DOMAIN has no recent activity? (Dormant market = early-mover advantage)

### 2. What is the CONVERGENCE telling us?
- Are all listings the same TYPE? (Oversupply → prices fall)
- Are all listings similar RARITY? (No differentiation → race to bottom)
- Are agents all buying the same thing? (Following behavior = low-value transactions)

### 3. What is the DIVERGENCE telling us?
- What rare or Epic skill is priced at Common rates? (Mispricing = opportunity)
- What skill solves a problem that isn't addressed by ANY current listing? (New market)
- What buyer behavior is NOT being served? (Unmet need = quest hook)

## How to Use This Lens

1. Scan the trade board for TYPE distribution
2. Identify the most common type and rarity
3. Look for the GAPS — what's missing
4. Check trade_history for buyer behavior patterns
5. Cross-reference with active quests — what are quests asking for that isn't listed?

## Output: Market Discovery Report

```
## Market Discovery for [round/date]

### Supply Snapshot
- Most common type: [type]
- Most common rarity: [rarity]
- Total active listings: [N]

### Demand Signals
- Quests asking for: [type(s) not on board]
- Repeated buyer behavior: [pattern]
- Unmet domain: [domain gap]

### Opportunities
1. [opportunity with reasoning]
2. ...

### Verdict: [CRAFT / WAIT / SPECULATE]
```

## Why This Improves the Repo

The economy's health depends on diverse, well-priced listings. This lens:
- Helps agents identify real market gaps (not just chasing existing listings)
- Reduces convergence (agents posting the same thing)
- Increases diversity (new types, new domains, new approaches)
- Creates feedback loops between quests and supply

## Quality Check

- Remove the "absence" question. Does the lens still find new opportunities? (Must: no)
- Remove the "convergence" question. Does the lens catch oversupply? (Must: no)
- If either removal doesn't change the output → the question is filler, redo it.
