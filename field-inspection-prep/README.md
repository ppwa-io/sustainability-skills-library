# Field Inspection Prep

Prepare technical field inspections for sustainability certifications, subsidy reconciliations, supplier audits, and similar regulatory site visits. Reconciles approved scope against supporting evidence (invoices, certificates of conformity, layouts) and generates a printable on-site inspection checklist plus a gaps report.

**Created by:** Borja Blanco Méndez (borja@azvai.com)

---

## Use case

For engineers, auditors, and ESG verifiers preparing on-site visits to projects that have been approved against a documented scope. Common scenarios:

- **Subsidy reconciliations** — verifying that what was funded by a public or private subsidy was actually built or installed, often across multiple annual reporting periods
- **Sustainability certifications** — preparing site visits for ISO, CE, B-Corp, or sector-specific certifications where physical evidence must match documented commitments
- **Supplier audits** — visiting a supplier facility to verify claims made in supplier questionnaires, scope 3 data submissions, or supply chain disclosures
- **Capital project inspections** — confirming that completed phases match approved drawings and specifications

The skill supports both **initial inspections** (first visit) and **re-inspections** (where a prior period was already verified and new construction may have buried earlier evidence under floors, walls, or finished surfaces).

---

## Best fit

- Multi-period inspections where evidence is scattered across folders by reporting period
- Provider-agnostic regulatory contexts (the skill localises document type names to your language and regulatory framework)
- Projects where folder structures are messy or inconsistent and a Claude assistant needs to locate the canonical "approved scope" document

## Less suited for

- Real-time on-site logging (this skill prepares the visit; it doesn't replace the on-site checklist app)
- Highly automated batch audits across many projects (the skill is direct-reading by design, one project at a time)

---

## How it works

The skill is **direct-reading**: default behaviour is to open PDFs and Excel files directly rather than running scripts, because every project folder has its own quirks. It exposes six commands:

| Command | What it does |
|---|---|
| `locate` | Scans the project folder for the approved scope document and supporting evidence |
| `extract` | Reads the approved scope and produces a structured list of items (ID, description, value, period, required evidence) |
| `reinspect` | For re-visits: flags previously verified items as out-of-scope, identifies items now buried/inaccessible, builds the focus list for the current visit |
| `checklist` | Generates the on-site inspection checklist as a printable Markdown document, sorted by physical location |
| `print` | Renders the checklist to a print-ready HTML/PDF using the included `md_to_print_html.py` helper |
| `post-visit` | After the inspection: updates project learnings, records new heuristics, generates a gaps report for items that could not be verified |

The skill can also build on optional `CLAUDE.md`, `LEARNINGS.md`, and `patterns.json` files in your project root. When present, these capture project-specific conventions so subsequent inspections inherit your accumulated knowledge.

---

## Example

**Setup:**
```
inspections-root/
└── PE201A-2024-00042/
    ├── APPLICATION/
    │   └── original-application.pdf
    ├── FINAL_REPORT/
    │   └── final-scope-2024.pdf
    ├── amendments/
    │   └── amendment-001.pdf
    ├── CERTIFICATES/
    │   ├── CE-aerator-pump.pdf
    │   └── ISO-14001-supplier.pdf
    └── invoices/
        ├── 2024/
        └── 2025/
```

**Input:**
> Prepare the re-inspection for PE201A-2024-00042. The 2024 annuity was already verified last year; we're inspecting the 2025 annuity now.

**What happens:**
1. `locate` finds `FINAL_REPORT/final-scope-2024.pdf` as the approved scope, plus the amendment and certificates
2. `extract` produces a structured item list (e.g. "Item 14: Industrial aerator pump, approved value €18,200, annuity 2025, evidence required: invoice + CE certificate + photo")
3. `reinspect` marks 2024 items out-of-scope and flags items that may now be buried (e.g. "Item 8: Drainage channel — likely covered by 2025 flooring work")
4. `checklist` produces a print-ready checklist for the 2025 items, sorted by physical location for an efficient site walk
5. After the visit, `post-visit` records what couldn't be verified (e.g. "Item 14: pump installed but serial number plate obscured by insulation — needs photo from supplier")

---

## Dependencies

**Almost zero.** The skill is direct-reading — Claude opens PDFs and Excel files via its built-in tools. The only helper script is `md_to_print_html.py` for rendering the final checklist to print-ready HTML.

Optional Python dependency for the print step: a Markdown → HTML library (typically `markdown` or equivalent — the script imports it on-demand).

**No API keys required.** Everything runs locally on the inspection folder.

---

## Installation

This is a Claude Code skill. To install:

```bash
# Project-scoped (typical: inside your inspections workspace)
cp -r field-inspection-prep <your-inspections-root>/.claude/skills/

# User-scoped (available across all your projects)
cp -r field-inspection-prep ~/.claude/skills/
```

No setup wizard. The skill runs against whichever project folder Claude is pointed at.

---

## Project folder conventions

The skill assumes (but does not require) a project layout like:

```
<your-inspection-root>/
├── PROJECT-ID-YYYY-NNNNN/
│   ├── CLAUDE.md            # project-specific context (optional)
│   ├── LEARNINGS.md         # accumulated lessons (optional)
│   ├── patterns.json        # heuristics (optional)
│   ├── APPLICATION/         # initial application documents
│   ├── FINAL_REPORT/        # final justification report
│   ├── amendments/          # scope amendments
│   ├── CERTIFICATES/        # certificates of conformity (CE, ISO, B-Corp, etc.)
│   └── invoices/            # per-period invoices
```

Adapt folder names to your own conventions; the skill reads what's there rather than requiring a specific structure.

---

## Background

Originally built for a regional public-subsidy inspection workflow on aquaculture and food-processing facilities (multi-annuity capital projects with mandatory technical verification before payment release). Generalised for public release. The principles transfer cleanly to any inspection where you need to reconcile what was approved against what was actually built or supplied.

---

## License

MIT (per library default).
