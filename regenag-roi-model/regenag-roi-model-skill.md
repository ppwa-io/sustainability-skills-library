---
name: regenag-roi-model
description: >
  Builds a structured 5–10 year financial comparison between regenerative and conventional
  agricultural sourcing, modelling transition costs, input cost trajectories, yield resilience,
  and Scope 3 carbon sequestration value. Use when a client needs to make the internal business
  case for regenerative sourcing to procurement leads, Chief Financial Officers (CFOs), or
  sustainability committees and requires numbers, not just narrative. Trigger phrases include:
  "build a regenerative sourcing ROI model", "make the financial case for regen sourcing",
  "model the cost of transitioning to regenerative", "compare conventional vs regenerative costs".
category: Reporting & Disclosure
framework_alignment: GHG Protocol | SBTi | General
audience_level: Intermediate
claude_interface: Claude.ai
---

# Regenerative Sourcing Return on Investment (ROI) Model — Skill

**Description:** Builds a structured 5–10 year financial comparison between regenerative and conventional agricultural sourcing. Models transition costs, input cost hedging, yield resilience during climate-stress years, and Scope 3 carbon sequestration value. Produces a presentation-ready summary for procurement or finance teams.

**When to use:** When one is making the internal business case for regenerative sourcing — to procurement leads, Chief Financial Officers (CFOs), or sustainability committees — and needs numbers, not just narrative.

**Created by:** Rochelle March, PPWA (rochelle@ppwa.io)

---

## How to use this skill

1. Open Claude and share this file as context
2. Provide the inputs listed below (paste directly into chat or upload a spreadsheet)
3. Ask Claude: *"Build a regenerative sourcing ROI model using the inputs I've provided and the RegenAg ROI Model skill"*

---

## Inputs to provide

Before Claude can build the model, gather the following. Estimates are acceptable — note where figures are estimated versus confirmed.

| Input | Description | Example |
|-------|-------------|---------|
| Commodity | Crop or ingredient being sourced | Corn, oats, almonds |
| Annual volume | Metric tons purchased per year | 100,000 MT |
| Current unit cost | Cost per metric ton, conventional source | $280/MT |
| Regenerative premium | Estimated price premium during transition (%) | 8–12% |
| Supply shortfall history | How often shortfalls have occurred (years out of 10) | 2 of last 10 years |
| Emergency premium | Cost premium paid during emergency sourcing events (%) | 25% |
| Scope 3 target | Whether the organization has a Scope 3 emissions reduction commitment | Yes / No |
| Planning horizon | Years to model | 5 or 10 |
| Geography / crop stress profile | Key sourcing regions and known climate risks | US Midwest, drought risk |

---

## What Claude will build

### Section 1 — Baseline vs Regenerative Cost Comparison
- Year-by-year input cost comparison (conventional vs regenerative)
- Transition period adjustment (years 1–5 yield gap modelled at –5 to –15%)
- Long-term input cost advantage: regenerative systems typically run 20–43% lower input costs than conventional equivalents, based on published field evidence

### Section 2 — Supply Resilience Value
- Emergency procurement risk model: probability of shortfall × volume × emergency premium
- Resilience uplift: regenerative systems show 25% lower yield variability and consistently outperform conventional in drought years
- Estimated annual expected cost of supply disruption, before and after regenerative transition

### Section 3 — Scope 3 Sequestration Value (if applicable)
- Estimated carbon sequestration: 0.3–0.7 tonnes of carbon dioxide equivalent (tCO2e) per acre per year
- Mapped against the organization's Scope 3 accounting needs
- Optional: indicative carbon credit value at current voluntary carbon market rates

### Section 4 — 5 or 10 Year Summary
- Total cost of conventional sourcing (including disruption risk)
- Total cost of regenerative sourcing (including transition premium)
- Net advantage / payback period
- Narrative framing for procurement or board presentation

---

## Output format

```
# Regenerative Sourcing ROI Model
**Client:** [name] | **Commodity:** [crop] | **Modelled:** [date]

## Assumptions & Inputs
[Table of all inputs provided, with source notes]

## Year-by-Year Cost Comparison
[Table: Year | Conv. cost | Regen. cost | Difference | Cumulative advantage]

## Supply Resilience Value
[Shortfall risk model and annual expected savings]

## Scope 3 Value (if applicable)
[Sequestration estimate and accounting relevance]

## 5 / 10 Year Summary
[Plain-language summary with net figures and payback period]

## Key Caveats
[Assumptions, data gaps, and recommended next steps]

---
*Model built using PPWA RegenAg ROI Skill | Sources: published field evidence cited in PPWA Insight — The ROI of Regenerative Agriculture (May 2026)*
```

---

## Evidence grounding

This model draws on the evidence base synthesised in *The ROI of Regenerative Agriculture* (Zahraie & March, PPWA, May 2026), which reviewed 495 peer-reviewed field studies. Key benchmarks used:

- **Input cost reduction:** 20–43% lower than conventional (LaCanne & Lundgren, 2018; Jacobs et al., 2022)
- **Net profit uplift:** 20–78% higher over comparable horizons
- **Yield resilience in drought years:** 7–22% above conventional (Gaudin et al., 2015)
- **Yield variability reduction:** ~25% lower in established regenerative systems
- **Carbon sequestration:** 0.3–0.7 tCO2e per acre per year (Kenne & Kloot, 2019; Vendig et al., 2023)
- **Transition period:** Years 1–5 typically involve yield adjustment; comparable performance from mid-transition onward (Poudel et al., 2001)

---

## Important notes

- This model produces estimates, not audited financials. All figures should be validated against client-specific data before being used in formal procurement or investment decisions.
- Where client data is unavailable, Claude will use published benchmark ranges and flag clearly.
- For supplier-level data infrastructure, pair this skill with the **Regenerative Supplier Sustainability Assessment Skill**.

---

*This skill is part of the PPWA RegenAg Toolkit. Pair with: Supplier Sustainability Assessment Skill · Research Synthesis Skill.*
