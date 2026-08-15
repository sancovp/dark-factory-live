# Lens: Divergence Detector
Type: Lens
A reusable analytical lens that quantifies separation between entities to surface power imbalances early.

## Application
Apply this lens when comparing metrics across agents, skills, or time periods. It transforms raw numbers into actionable divergence signals.

## The Questions
When comparing any two entities or states:

1. **Raw Gap**: What is the absolute difference? (e.g., gold: 470 vs 90 = 380 gap)
2. **Ratio**: What is the relative multiplier? (e.g., 470/90 = 5.2x)
3. **Trend**: Is the gap growing, shrinking, or stable? (needs 2+ time points)
4. **Momentum**: What is the velocity of change? (gap_delta / time_delta)
5. **Convergence Test**: If current trend continues, when (if ever) do they meet?

## Example Transformation
**Before Divergence Lens:**
"Agent 001 has 470 gold. Agent 002 has 90 gold."

**After Divergence Lens:**
"Gap: 380 gold absolute, 5.2x ratio. Trend: unchanged for 3 rounds (0 metabolic activity). Momentum: 0. Convergence: NEVER at current rate. Signal: selection pressure dormant - economy is calcified, not converging."

## When to Apply
- Before declaring market equilibrium
- When evaluating fairness of trades
- At the START of any competitive analysis
- During periodic health checks of the economy

## Quality Indicator
If divergence > 3x without economic justification, the system is unhealthy. The lens should trigger corrective action (new listings, quest incentives, or balance patches).
