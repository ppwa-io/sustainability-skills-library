---
name: regenag-research-synthesis
description: >
  Searches and synthesises recent peer-reviewed evidence on regenerative agriculture outcomes —
  filtered by crop type, geography, and farming system — to support a specific sourcing or
  procurement decision. Use when a client needs to make an evidence-based case for regenerative
  sourcing for a specific crop or region and the available literature feels scattered, inaccessible,
  or too academic for direct business use. Trigger phrases include: "find the evidence on regenerative
  farming for [crop]", "what does the research say about regen ag in [region]", "build an evidence
  brief for regenerative sourcing", "synthesise the literature on regenerative [outcome]".
category: Reporting & Disclosure
framework_alignment: General
audience_level: Intermediate
claude_interface: Claude.ai
---

# Regenerative Agriculture Research Synthesis — Skill

**Description:** Searches and synthesises recent peer-reviewed evidence on regenerative agriculture outcomes — filtered by crop type, geography, and farming system — to support a specific sourcing or procurement decision. Produces a concise, cited evidence brief ready for internal use or client presentation.

**When to use:** When one is making an evidence-based case for regenerative sourcing for a specific crop or region, and the available literature feels scattered, inaccessible, or too academic to use directly in a business context.

**Created by:** Rochelle March, PPWA (rochelle@ppwa.io)

---

## How to use this skill

1. Open Claude and share this file as context
2. Provide the synthesis parameters below
3. Ask Claude: *"Run a regenerative agriculture research synthesis using the parameters I've provided and the RegenAg Research Synthesis skill"*

Claude will run targeted searches, filter for credible and recent sources, and produce a structured evidence brief.

---

## Inputs to provide

| Parameter | Description | Example |
|-----------|-------------|---------|
| Crop / commodity | The specific crop or ingredient | Oats, almonds, soybeans, wheat |
| Geography | Primary sourcing region(s) | US Midwest, Sub-Saharan Africa, Southern Europe |
| Key question | The decision or claim you need evidence for | "Does regenerative farming improve drought resilience for oats in the Northern Plains?" |
| Outcome focus | Which outcomes matter most | Yield, profitability, water, carbon, input costs, resilience |
| Audience | Who will read this brief | Internal procurement team, board, external client, investor |
| Time horizon | Short-term (1–3 years) or long-term (5–20 years) | Long-term |

---

## What Claude will research

Claude will run 6–10 targeted searches across:

- **Academic databases:** Google Scholar, PubMed, Web of Science (recent results prioritised)
- **Preprint servers:** arXiv, bioRxiv (for cutting-edge findings not yet peer-reviewed — flagged clearly)
- **Institutional reports:** Food and Agriculture Organization (FAO), Intergovernmental Panel on Climate Change (IPCC), International Food Policy Research Institute (IFPRI), Rodale Institute, land-grant university extension programs
- **Meta-analyses and systematic reviews:** Prioritised where available, as they synthesise across many individual studies

Search queries will be scoped to the specific crop, geography, and outcome focus provided. Claude will note publication dates and flag any findings older than 5 years that are included due to limited recent evidence.

---

## Quality filters applied

Claude will apply the following filters before including a source:

- **Peer-reviewed or institutional:** No blog posts, press releases, or industry marketing materials unless flagged as practitioner context
- **Field-based evidence preferred:** Lab results and modelling studies included but distinguished from field trials
- **Sample size noted:** Studies with very small samples (fewer than 5 farm sites) flagged
- **Geographic relevance:** Studies from the requested region prioritised; analogous geographies noted where direct evidence is thin
- **Conflict of interest check:** Funding sources noted where disclosed; industry-funded studies flagged

---

## Output format

```
# Regenerative Agriculture Evidence Brief
**Crop:** [crop] | **Region:** [geography] | **Question:** [key question]
**Prepared for:** [audience] | **Date:** [date]

## Executive Summary
[3–5 sentences: what the evidence shows, how strong it is, and what it means for the decision at hand]

## Evidence Overview

### Yield Performance
[2–4 bullet points, each with: finding | source | date | study type | caveats]

### Profitability & Input Costs
[2–4 bullet points, same format]

### Water Resilience
[2–4 bullet points, same format]

### Carbon Sequestration
[2–4 bullet points, same format]

### [Additional outcome if requested]
[2–4 bullet points, same format]

## Strength of Evidence Assessment
[Plain-language summary: how consistent is the evidence? Where are the gaps? What would strengthen the case?]

| Outcome | Evidence strength | No. of sources | Key gaps |
|---------|-----------------|----------------|----------|
| Yield | Strong / Moderate / Limited | N | |
| Profitability | | | |
| Water resilience | | | |
| Carbon | | | |

## Implications for [Client / Decision context]
[3–5 bullet points translating the evidence into practical implications for the specific sourcing or procurement decision]

## Recommended Next Steps
[2–3 specific actions: additional data to gather, supplier questions to ask, platforms to explore]

## Sources
[Full citation list, alphabetical]

---
*Research synthesis produced using PPWA RegenAg Research Synthesis Skill*
*Searches run: [list exact queries used]*
*All sources verified as of [date]*
```

---

## Evidence strength guide

| Rating | Meaning |
|--------|---------|
| **Strong** | Multiple peer-reviewed studies from the relevant geography; consistent findings; includes at least one meta-analysis |
| **Moderate** | Several studies; some geographic or crop-type variation; findings directionally consistent |
| **Limited** | Few studies; findings from analogous geographies; or older evidence base (5+ years) |
| **Insufficient** | Fewer than 2 credible sources found; synthesis not possible — note clearly and suggest alternatives |

---

## Important notes

- This skill produces a research brief, not a systematic review. It is designed for practical use in business and consulting contexts, not academic publication.
- Where evidence is thin for a specific crop or geography, Claude will say so clearly and suggest the closest available analogues rather than overstate the case.
- For translating evidence into financial projections, pair with the **Regenerative Sourcing ROI Model Skill**. For supplier-level assessment, pair with the **Regenerative Supplier Sustainability Assessment Skill**.

---

*This skill is part of the PPWA RegenAg Toolkit. Pair with: ROI Model Skill · Supplier Assessment Skill.*
