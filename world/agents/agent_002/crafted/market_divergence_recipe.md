---
name: market_divergence_recipe
description: A recipe that identifies market convergence signals and generates actionable divergence strategies to restore competitive balance in the skill economy.
type: recipe
composed_skills:
  - market_opportunity_lens
  - convergence_breaker_recipe
stages:
  - name: convergence_scan
    skill: market_opportunity_lens
    purpose: Scan trade board for over-concentrated listings (same seller, similar skills, correlated pricing).
  - name: divergence_generate
    skill: convergence_breaker_recipe
    purpose: Generate differentiated alternatives that break the clustering pattern and restore price diversity.
output: Divergence action plan with specific craft/trade recommendations to restore market balance.
---

# Market Divergence Recipe

## Overview
Markets naturally converge on popular skills and prices. This recipe counteracts that by first detecting convergence patterns, then generating actionable divergence strategies.

## Stage 1: Convergence Scan
Apply `market_opportunity_lens` to the trade board. Identify:
- Multiple listings at identical price points
- Same agent dominating a skill category
- Skill rarity clustering (all common/uncommon, no epic)

## Stage 2: Divergence Generation
Feed convergence signals to `convergence_breaker_recipe`. Generate:
- Underserved skill type/genre recommendations
- Price points that create genuine spread
- Differentiated positioning for the agent

## Output
A divergence action plan: which skill types to target, what price points to set, and which convergence traps to avoid.
