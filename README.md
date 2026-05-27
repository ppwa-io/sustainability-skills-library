# Claude Skills Library for Sustainability Professionals

An open-source library of **SKILL.md files** for sustainability practitioners working with [Claude](https://claude.ai) and [Claude Code](https://claude.ai/claude-code).

Skills are reusable instruction files that teach Claude a specific workflow once, so you stop re-writing context in every session. This library focuses on skills purpose-built for sustainability work: emissions accounting, disclosure reporting, supply chain analysis, stakeholder communication, and more.

---

## What is a SKILL.md?

A SKILL.md file is a structured prompt template that tells Claude exactly how to handle a specific, repeatable task. Instead of writing the same context into every conversation, you drop a skill into Claude Code or reference it in your prompt, and Claude executes the workflow correctly every time.

Skills are especially powerful for sustainability work because:

- Regulatory frameworks (GHG Protocol, CSRD, TCFD) require precise, consistent methodology
- Disclosure workflows involve the same document structures repeatedly
- Many practitioners are not developers, skills make AI workflows accessible without code

---

## Skill Categories

| Category | What's covered |
|---|---|
| **Emissions & Carbon Accounting** | Scope 1/2/3 calculations, spend-based EEIO (Environmentally-Extended Input-Output) methodology, emission factor lookups, and identifying where decarbonisation creates operational cost advantage |
| **Reporting & Disclosure** | GRI (Global Reporting Initiative), CSRD (Corporate Sustainability Reporting Directive)/ESRS, TCFD (Task Force on Climate-related Financial Disclosures), ISSB (International Sustainability Standards Board)/IFRS S1-S2 gap analysis and drafting, and translating disclosure data into board-level strategic narratives |
| **Procurement & Supply Chain** | Supplier data collection, Scope 3 Category 1 workflows, regenerative sourcing assessment, and building supply chain resilience intelligence beyond compliance screening |
| **Stakeholder Communication** | Board briefs, investor narratives, ESG (Environmental, Social, and Governance) summary documents, and framing sustainability performance as a driver of long-term business value |
| **Data Analysis & Visualization** | ESG data quality checks, benchmark analysis, dataset structuring, and surfacing insights that connect sustainability performance to financial and operational outcomes |
| **Document Production** | Proposals, scope-of-work documents, research commissions, and evidence briefs for internal business cases |
| **Research & Intelligence** | Regulatory monitoring, competitive landscape, literature synthesis, and scanning for emerging risks and opportunities before they reach mainstream reporting |
| **Strategy & Advisory** | Materiality assessment, target-setting frameworks, transition planning, and designing business systems where sustainability and resilience are built in by default |

---

## Using a Skill

Each skill is a self-contained folder with a `SKILL.md` file and any supporting assets.

**In Claude Code** (recommended for repeatable workflows):
```bash
# Project-scoped
cp -r <skill-folder> <your-project>/.claude/skills/

# User-scoped (available across all your projects)
cp -r <skill-folder> ~/.claude/skills/
```

**In Claude.ai** (for one-off use):
Copy the contents of `SKILL.md` into your conversation as context, then describe your task.

Each skill's own README includes any setup steps, required inputs, and example outputs.

---

## Contributing a Skill

Contributions are welcome. To submit a skill:

1. Fork this repository
2. Create a folder named after your skill (e.g., `scope3-category1-spend-based/`)
3. Include:
   - `SKILL.md`, the skill file itself, following the template below
   - `README.md`, a brief description, use case, example inputs/outputs, and any dependencies
4. Open a pull request with a short description of the workflow your skill covers

**Skill file template:**
```
---
name: your-skill-name
description: >
  One-sentence description of what this skill does and when to use it.
  Include trigger phrases, the kinds of requests that should invoke it.
category: [Emissions & Carbon Accounting | Reporting & Disclosure | ...]
framework_alignment: [GHG Protocol | GRI | CSRD | TCFD | TNFD | ISSB | SBTi | EU Taxonomy | General]
audience_level: [Beginner | Intermediate | Advanced]
claude_interface: [Claude.ai | Claude Code | API]
---

# Skill Title

[Skill instructions here]
```

---

## Guidelines for Contributors

- **Keep skills methodology-neutral** where possible, skills that follow published frameworks (GHG Protocol, GRI Standards) are more broadly useful than organization-specific workflows
- **Do not include proprietary data**, client-specific content, or confidential organizational information
- **Tested skills only**, please verify your skill produces correct output before submitting
- **Cite your sources**, if a skill implements a specific methodology, link to the source document in the README

---

## Skills Index

| Skill | Category | Framework | Level |
|---|---|---|---|
| AI × Sustainability Weekly Scan | Research & Intelligence | General | Beginner |
| Field Inspection Prep | Procurement & Supply Chain | General | Intermediate |
| Low-Computer Article Visuals | Data Analysis & Visualization | General | Advanced |
| RegenAg Research Synthesis | Procurement & Supply Chain | General | Intermediate |
| RegenAg ROI Model | Reporting & Disclosure | GHG Protocol \| SBTi \| General | Intermediate |
| RegenAg Supplier Assessment | Procurement & Supply Chain | GHG Protocol \| GRI \| General | Intermediate |
| Research Writing Assistant | Document Production | General | Advanced |
| *(more skills coming, submit a pull request!)* | | | |

---

## About This Library

This library was initiated by [PPWA](https://ppwa.io), a sustainable innovation studio with a goal to support sustainability professionals to use AI effectively without requiring a technical background.

If you have a sustainability workflow you'd like to see as a skill, [open an issue](../../issues/new) describing the use case.

---

## License

MIT. Use, modify, and republish freely. Attribution appreciated but not required.
