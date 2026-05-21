# Stage 5: Polish & Deliver

## Overview

Generate SEO meta data, run a final consistency pass, and deliver the article for review. Runs in the main thread.

## Step 0: Load References

Read `references/writing-guidelines.md` for the fluff blacklist and quality standards. Read the brand profile used in Stage 4. Read `skill_config.json` for `brand_name`.

## Step 1: Generate Meta Data

Read `draft.md` and `brief.json`. Generate SEO meta data.

### Meta Writer Prompt

Analyze the article content and produce:

- **meta_titles:** Generate **5 title options** with a **recommended pick**. Each ~60 characters max, include primary keyword once naturally. Vary formats: question, how-to, number, benefit-led, curiosity gap. Append brand name if space allows (e.g., " | {brand_name}" from `skill_config.json`).
- **meta_descriptions:** Generate **3-5 meta description options**. **130 characters maximum** (strict). **No year references**. Include primary keyword once. Soft CTA optional ("Learn...", "Discover...").
- **slug:** Include primary keyword, max 5-6 words, lowercase, hyphens, no special characters, no stop words, no trailing slash

### Output: `meta.json`

```json
{
  "meta_titles": [
    {"title": "string", "recommended": true},
    {"title": "string", "recommended": false}
  ],
  "meta_descriptions": [
    "string",
    "string",
    "string"
  ],
  "slug": "string"
}
```

## Step 2: Consistency Pass

Review `draft.md` for final polish:

### Heading Hierarchy Check
- Exactly one `#` (H1) — the title
- All major sections use `## `
- Subsections use `### `
- No skipped heading levels (no H1 → H3)

### CTA & Link Insertion
- If `cta_link` is set in `brief.json`, ensure a CTA is placed naturally (usually near the end, before FAQ)
- If `internal_links` are set, weave them naturally into relevant sections
- Don't force links — they should feel organic in context

### Final Quality Checks
- No em-dashes (—) anywhere in the article
- No orphaned editor notes (`[EDITOR NOTE: ...]` should all be resolved)
- No orphaned non-commodity flags (`[NON_COMMODITY DRIFT]`, `[COMMODITY RISK]`, `[NEEDS SOURCE]` must all be resolved or escalated to user)
- No fluff phrases from the blacklist in `references/writing-guidelines.md`
- Consistent formatting throughout (bold, lists, code blocks)
- FAQ is the last section
- Every section starts with an engaging hook (not a generic opener)

### Final Commodity Check

Before assembling `article.md`, run the Sullivan test on the whole article:

> "Could a competent SEO write a near-identical article in 2 hours from the SERP alone?"

If yes, the article is commodity. Surface this to the user with the option to add a non-commodity section before publishing. Note in `consistency-report.md`:

- `non_commodity_sections`: count of sections containing at least one named entity, original number, attributed quote, or specific incident
- `commodity_risk_level`: low / medium / high
- `recommended_recipe`: if commodity_risk is medium/high, suggest one specific non-commodity recipe by name (e.g. "Recipe 1 — pull X dataset, run Y analysis")

### Consistency Check Report

Save results to the working directory as `consistency-report.md` documenting:
- Em-dash count (must be 0)
- Fluff phrase count (must be 0, list any found)
- Heading hierarchy status (pass/fail + details)
- CTA insertion status (inserted/not needed/missing)
- Orphaned marker count (must be 0)
- Any other issues found

This report provides an audit trail that the consistency pass was actually run.

### Word Count Report

Calculate and report:
- Total word count vs target from `brief.json`
- Per-section word counts vs targets from `outline.json`
- Flag any sections that are >15% off target (writer/editor targeted ±10%; anything still >15% off needs attention)

## Step 3: Visuals

Before final assembly, ensure the article has the visuals it needs. If you have a programmatic image-generation skill installed (such as the companion `low-compute-article-visuals` skill in this library), call it here. Otherwise produce visuals separately or note image needs for downstream handling.

Decision tree:

1. **Data-anchored section?** (Check `outline.json.structure_decision.non_commodity_section_numbers` for sections with `non_commodity_anchor` referring to data.)
   - **Yes** → produce a branded chart (matplotlib or equivalent). Inline (SVG) plus a LinkedIn-square version (PNG 1080×1080) if the chart is the headline finding.
   - **No** → continue.

2. **Mid-body imagery?** (Most non-data articles need it — explainer, opinion, list posts.)
   - **Yes** → 1-3 open-license stock images (Unsplash, Pexels, or equivalent). Always paste the attribution markdown block alongside the image.
   - **No** → continue.

3. **Featured image** — always required for publishing. If a chart from step 1 is suitable, use it. Otherwise produce a branded title-card image (OG 1200×630 plus square 1080×1080 if needed).

4. **LinkedIn-square** — if the article will be shared on LinkedIn, produce a 1080×1080 version of either the chart or the featured image.

**Brand auto-detection:** read `brief.json` for `brand_profile` or infer from the article's target site URL. If unclear, ask the user. Brand profiles are defined per-project in `references/brand-profile.md`.

## Step 4: Final Assembly

1. Save the polished article to `article.md`
2. Present to the user with a summary:
   - Word count (total and per-section)
   - Meta data (title, description, slug)
   - Visual deliverables (featured image, charts, stock images, LinkedIn squares — paths to each)
   - Any flags or concerns
   - Sections that might need attention

## User Approval Gate

Use **AskUserQuestion**:
- "Approve — article is ready"
- "Revise sections" (user specifies which sections to rework — loop back to Stage 4 for targeted writer/editor pass)
- "Revise meta" (user provides meta changes)

## Stage Complete

Final working directory:
```
keyword-slug-date/
├── brief.json
├── competitors/
├── gap-analysis.json
├── research.json
├── outline.json
├── draft-v1.md
├── editor-notes.md
├── draft-v2.md
├── draft.md
├── article.md                      ← final article
├── meta.json                       ← SEO meta data
├── featured-image.png / .jpg       ← featured image (always)
├── chart_<topic>.py                ← chart script (if data article)
├── chart-<topic>.svg / .png        ← chart outputs (if applicable)
├── chart-<topic>-linkedin.png      ← LinkedIn square (if applicable)
├── images/                         ← stock photos (if applicable)
│   └── <slug>.attribution.md
└── consistency-report.md
```
