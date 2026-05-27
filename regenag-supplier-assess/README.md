# RegenAg Supplier Assessment Skill

**Part of the PPWA RegenAg Toolkit** | Created by Rochelle March, PPWA (rochelle@ppwa.io)

## What this skill does

Evaluates and scores ingredient suppliers on regenerative agriculture readiness using a three-tier question framework: 1.) standard asks, 2.) stretch asks, and 3.) forward-looking asks. Produces a structured scorecard across five dimensions: practice maturity, input cost resilience, water performance, emissions transparency, and transition readiness. Designed to work with information already available from RFP responses, sustainability reports, or supplier interviews.

## When to use it

- Evaluating or onboarding ingredient suppliers against regenerative sourcing criteria
- Building a supplier shortlist for a regenerative sourcing strategy
- Generating scored supplier data for Environmental, Social and Governance (ESG) or sustainability reporting
- Comparing multiple suppliers to prioritise engagement

**Trigger phrases:** "assess this supplier on regenerative practices" · "score our suppliers on regen ag readiness" · "build a supplier scorecard for regenerative sourcing" · "compare suppliers on sustainability" · "evaluate supplier ESG data quality"

## Dependencies

- No external tools required
- Input can be pasted from RFP responses, sustainability reports, or interview notes
- Pair with **RegenAg ROI Model Skill** to connect supplier practice data to financial projections
- Pair with **RegenAg Research Synthesis Skill** to benchmark supplier claims against published field evidence

## Example inputs

```
Supplier: Greenfield Grains Co.
Commodity: Oats
Geography: Minnesota, USA
Volume: 15,000 MT/year

Practices: No-till for 4 years; cover cropping in year 3 onward; enrolled in Regrow program
Input costs: Stable over past 3 years; synthetic fertiliser use decreasing
Water: Irrigation scheduling in place; no significant drought losses reported
Emissions: Not currently tracked; plans to begin Scope 1 tracking in 2026
Transition: Incremental adoption since 2020; no formal targets set
```

## Example output (scorecard)

```
# Regenerative Supplier Assessment
**Supplier:** Greenfield Grains Co. | **Commodity:** Oats | **Assessed:** May 2026

## Summary Scorecard
| Dimension            | Score (1–5) | Tier evidence available | Key gaps                        |
|----------------------|-------------|-------------------------|---------------------------------|
| Practice maturity    | 4           | Tier 1–2                | No soil health monitoring data  |
| Input cost resilience| 3           | Tier 1, Tier 3          | Directional only                |
| Water performance    | 3           | Tier 1                  | No infiltration data            |
| Emissions transparency| 2          | Tier 3 only             | No current tracking             |
| Transition readiness | 3           | Tier 1, Tier 3          | No formal targets               |

## Overall Score: 3.1 / 5 — Emerging

## Sourcing Recommendation: Develop
Greenfield Grains shows credible Tier 1–2 practice adoption and a realistic emissions tracking
plan. The absence of formal targets limits the score, but direction of travel is positive.
Recommended for active supplier development engagement.
```

## Pull request description

> Adds the PPWA RegenAg Supplier Assessment skill. Covers tiered evaluation of ingredient suppliers across five regenerative practice dimensions, producing a structured scorecard and sourcing recommendation. Designed to work with information from RFPs, sustainability reports, and interviews with no financial disclosure required from suppliers. Includes multi-supplier comparison capability.

