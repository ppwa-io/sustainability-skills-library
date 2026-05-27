# RegenAg Research Synthesis Skill

**Part of the PPWA RegenAg Toolkit** | Created by Rochelle March, PPWA (rochelle@ppwa.io)

## What this skill does

Runs targeted searches across peer-reviewed databases and institutional sources, then synthesises the findings into a concise, cited evidence brief filtered by crop, geography, and outcome focus. Designed to make academic literature directly usable in procurement and business contexts.

## When to use it

- A client needs to make an evidence-based case for regenerative sourcing for a specific crop or region
- A procurement or sustainability team needs a credible literature summary for internal or board use
- Available research feels too scattered or technical to use directly in a client-facing document

**Trigger phrases:** "find the evidence on regenerative farming for [crop]" · "what does the research say about regen ag in [region]" · "build an evidence brief for regenerative sourcing" · "synthesise the literature on regenerative [outcome]"

## Dependencies

- Requires web search access in Claude (enabled by default on Claude.ai)
- Pair with [**RegenAg ROI Model Skill**](https://github.com/ppwa-io/sustainability-skills-library/tree/main/regenag-roi-model) to translate evidence into financial projections
- Pair with [**RegenAg Supplier Assessment Skill**](https://github.com/ppwa-io/sustainability-skills-library/tree/main/regenag-supplier-assess) to link evidence benchmarks to supplier scoring

## Example inputs

```
Crop / commodity: Oats
Geography: Northern Plains, USA
Key question: Does regenerative farming improve drought resilience for oats in the Northern Plains?
Outcome focus: Yield resilience, water performance, input costs
Audience: Internal procurement team
Time horizon: Long-term (5–20 years)
```

## Example output (evidence overview excerpt)

```
# Regenerative Agriculture Evidence Brief
**Crop:** Oats | **Region:** Northern Plains, USA
**Question:** Does regenerative farming improve drought resilience for oats in the Northern Plains?

## Strength of Evidence Assessment

| Outcome        | Evidence strength | No. of sources | Key gaps                          |
|----------------|-------------------|----------------|-----------------------------------|
| Yield          | Moderate          | 6              | Limited oat-specific trials       |
| Water resilience | Strong          | 8              | Most data from wheat/corn systems |
| Input costs    | Moderate          | 4              | Few Northern Plains-specific studies |
```

## Pull request description

> Adds the PPWA RegenAg Research Synthesis skill. Covers targeted literature search and synthesis across peer-reviewed databases and institutional sources, filtered by crop, geography, and outcome focus. Produces a cited evidence brief formatted for procurement and business audiences. Includes evidence strength ratings and quality filters.

