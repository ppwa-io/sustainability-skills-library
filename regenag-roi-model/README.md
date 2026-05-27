# RegenAg ROI Model Skill

**Part of the PPWA RegenAg Toolkit** | Created by Rochelle March, PPWA (rochelle@ppwa.io)

## What this skill does

Builds a structured 5–10 year financial model comparing regenerative and conventional agricultural sourcing. Designed for use in procurement and finance contexts where a quantified business case is required.

## When to use it

- A procurement team needs to justify regenerative sourcing co-investment to a Chief Financial Officer (CFO) or finance committee
- A sustainability lead needs to monetise supply resilience risk and Scope 3 sequestration value
- A client wants a payback period estimate before committing to a regenerative supplier transition

**Trigger phrases:** "build a regenerative sourcing ROI model" · "make the financial case for regen sourcing" · "model the cost of transitioning to regenerative" · "compare conventional vs regenerative costs"

## Dependencies

- No external tools required
- Pair with **RegenAg Supplier Assessment Skill** to connect financial model inputs to live supplier data
- Pair with **RegenAg Research Synthesis Skill** to ground yield and resilience assumptions in the latest field evidence

## Example inputs

```
Commodity: Oats
Annual volume: 40,000 MT
Current unit cost: $310/MT
Regenerative premium: 10%
Supply shortfall history: 2 of last 10 years
Emergency premium: 20%
Scope 3 target: Yes
Planning horizon: 10 years
Geography: Northern Plains, USA — drought risk
```

## Example output (summary section)

```
# Regenerative Sourcing ROI Model
**Client:** Acme Foods | **Commodity:** Oats | **Modelled:** May 2026

## 10-Year Summary
Conventional sourcing total cost (including disruption risk): $131.4M
Regenerative sourcing total cost (including transition premium): $118.7M
Net advantage of regenerative: $12.7M over 10 years
Payback period: Year 6

Scope 3 sequestration value (at $15/tCO2e): $1.1M over 10 years
```

## Pull request description

> Adds the PPWA RegenAg ROI Model skill. Covers 5–10 year cost modelling for regenerative vs conventional sourcing, including transition premium, supply resilience risk, and Scope 3 sequestration value. Evidence-grounded using benchmarks from 495 peer-reviewed studies. Designed for procurement and finance audiences.

