# Low-Compute Article Visuals

A Claude Code skill for producing publish-ready images programmatically. Built for sustainability reports, ESG dashboards, and consulting articles where visuals are recurring and the cost of regenerating them with AI image models adds up. **Skip AI image generation for charts, stat cards, and structured visuals — typically ~97% less compute, cost, and energy.**

**Created by:** Borja Blanco Méndez (borja@azvai.com)

---

## What it does

Five modes, one toolchain:

| Mode | Use case | Tech |
|---|---|---|
| **chart** | Branded analytics charts (bar, stacked, time series, grouped, donut) | matplotlib |
| **featured** | OG-card / title-card images for articles | matplotlib + Pillow |
| **html-image** | Stat cards, social cards, anything HTML+CSS rendered to PNG | html2image (headless Chrome) |
| **stock** | Free-license stock photos with attribution | Unsplash + Pexels APIs |
| **linkedin-square** | 1080×1080 LinkedIn-ready wrapper around any of the above | matplotlib |

All five modes use a shared **brand profile** (colors, fonts, attribution template, watermark) so output is consistent across an article, a campaign, or a client.

---

## Why programmatic over AI image generation

For structured visuals — charts, stat cards, branded title cards, social images — AI image generation is the wrong tool:

- DALL-E 3 charges $0.04 to $0.12 per image. Gemini Imagen ranges from $0.02 to $0.24.
- Each image runs ~3 Wh of compute energy ([2026 study](https://arxiv.org/abs/2506.17016)).
- 3-5 iterations per image to land the right look.
- Output is generic, not brand-aware.

This skill produces equivalent or better visuals for ~$0 in cloud cost and ~0.01 Wh of local compute, with brand colors and fonts consistently applied. AI image generation is still useful for genuine photographic outputs (photorealistic compositions, custom photo edits) — keep it for that.

---

## Use case

For sustainability communicators, ESG analysts, and consulting teams who produce visual content regularly: research charts for reports, stat cards for blog posts, OG images for social shares, stock photography for explainers. The skill replaces three patterns at once:

1. Cloning and editing a Python script every time you need a new chart
2. Reaching for DALL-E / Imagen for visuals that aren't really photographic (which adds cost and burns compute for inferior output)
3. Hand-coding HTML in a browser tab to screenshot a stat card

The "low-compute" framing is literal: programmatic rendering uses ~0.01 Wh per image versus ~3 Wh for an AI image model — a measurable energy footprint difference at scale.

Pairs naturally with the companion `research-writing-assistant` skill (also in this library), which can call into this skill in its final stage to produce article visuals.

---

## Quick start

```bash
# 1. Install dependencies (one-time)
pip install -r scripts/requirements.txt

# 2. Set up your brand (interactive wizard)
python scripts/setup_brand.py
# ...or non-interactive
python scripts/setup_brand.py --non-interactive --slug acme \
    --name "Acme Sustainability" --primary "#10b981"

# 3. Verify the brand looks right
python scripts/preview_brand.py --brand acme

# 4. Use any mode
python scripts/cli.py featured --brand acme --title "My article" --out featured
python scripts/cli.py html --template title_card.html --brand acme \
    --vars '{"title":"How AI in L&D Really Works"}' --output title.png
python scripts/cli.py stock --query "wind turbines at dusk" --count 3
```

For chart-specific work, copy a chart template into your article working directory and edit the data:

```bash
cp scripts/chart_template.py /path/to/article/chart_my_topic.py
# edit DATA, CONFIG, render
python /path/to/article/chart_my_topic.py
```

---

## Brand profiles

Brand profiles live in `brands/<slug>.json`. The library ships with a `_default.json` example. Each profile defines:

- **Colors**: accent, dark, light, pop, benchmark, plus a 6-color data palette
- **Fonts**: a CSS font stack (e.g. `["DM Sans", "Helvetica", "Arial", "sans-serif"]`)
- **Attribution template**: how source lines render (`Source: {source}, analysis by <your-brand>.com`)
- **Watermark**: optional brand text rendered in the corner of charts

The `setup_brand.py` wizard validates colors, generates a default data palette, and saves a swatch preview alongside the JSON. The `preview_brand.py` script renders all chart types in your brand for a quick sanity check.

---

## Example

**Input:**
> Generate a horizontal bar chart of "Scope 3 emissions by category" for our Q1 report. Five categories: Purchased goods (52%), Business travel (18%), Employee commuting (12%), Capital goods (10%), Other (8%). Brand: acme.

**What happens:**
1. The skill copies `chart_template.py` into your working directory
2. Pre-fills the DATA dict with your five categories and percentages
3. Loads the `acme` brand profile (colors, fonts, attribution template)
4. Renders both SVG (inline use) and PNG (featured) at 1200×675

**Output:**
```
working_dir/
├── chart_scope3_by_category.svg     # inline, sharp at any size
├── chart_scope3_by_category.png     # 1200×675 OG card size
└── chart_scope3_by_category.py      # editable source (re-run if data changes)
```

Total runtime: under 2 seconds. Energy footprint: ~0.01 Wh.

---

## Modes in detail

Each mode has its own reference doc in `references/`:

- [`mode-chart.md`](references/mode-chart.md) — copy-and-edit Python chart templates
- [`mode-featured.md`](references/mode-featured.md) — branded title cards
- [`mode-html-image.md`](references/mode-html-image.md) — render HTML templates to PNG
- [`mode-stock.md`](references/mode-stock.md) — Unsplash + Pexels stock search
- [`mode-linkedin-square.md`](references/mode-linkedin-square.md) — square-format wrapper

---

## Dependencies

Python 3.9+ and the packages listed in `scripts/requirements.txt`:

- `matplotlib` (charts, featured images)
- `Pillow` (image composition)
- `html2image` (HTML → PNG, requires Chrome/Chromium)
- `requests`, `python-dotenv` (stock mode)

Install with `pip install -r scripts/requirements.txt`.

For `html-image` mode you also need Chrome / Chromium installed locally (most desktops already have this; html2image shells out to it).

### API keys (stock mode only)

| Variable | Required for | Where to get one |
|---|---|---|
| `UNSPLASH_ACCESS_KEY` | `stock` mode (preferred source) | https://unsplash.com/developers |
| `PEXELS_API_KEY` | `stock` mode (fallback or alternative source) | https://www.pexels.com/api/ |

Add to `.env` at the project root. Both are free.

`chart`, `featured`, `html-image`, and `linkedin-square` modes need **no API keys** — they run entirely locally.

---

## Installation

This is a Claude Code skill (folder-based with scripts and templates). To install:

```bash
# Project-scoped
cp -r low-compute-article-visuals <your-project>/.claude/skills/

# User-scoped (available across all your projects)
cp -r low-compute-article-visuals ~/.claude/skills/
```

Then run `pip install -r low-compute-article-visuals/scripts/requirements.txt` once, set up a brand with `python low-compute-article-visuals/scripts/setup_brand.py`, and you're ready.

---

## Source attribution

Every visual that uses external data or photography should cite its source. The skill handles this:

- **Charts**: source line rendered in the bottom-left of the chart, in brand color and style
- **Stock photos**: a markdown attribution block is generated alongside each downloaded image, with proper photographer credit and platform link
- **Featured images**: typically don't need attribution; you control the `subtitle` content

---

## Methodology source

The energy and cost comparisons against AI image generation are documented in the article ["How Claude Code Skills Cut AI Energy Use"](https://azvai.com/claude-code-skills-cut-ai-energy-use/), with measurement methodology and citations.

---

## License

MIT (per library default). Brand profiles and chart templates are designed to be copied, modified, and republished — that's the point.
