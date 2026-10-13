# DP-750 Azure Databricks — Practice Exam Bank

A self-contained, printable study bank of **75 practice questions** for the Microsoft
**DP-750: Implementing Data Engineering Solutions Using Azure Databricks** exam.

Each question ships with the four answer options, the highlighted correct answer, a
justification, and a breakdown of why every other option is wrong — all cross-referenced
to the corresponding Microsoft Learn module.

The document is available in **two languages**, French and Brazilian Portuguese, on a single
static site.

## Live site

| Language | URL |
| --- | --- |
| Français | https://eliswilliam.github.io/dp750-azure-databricks-exam/ |
| Português (BR) | https://eliswilliam.github.io/dp750-azure-databricks-exam/pt.html |

## Features

- **75 questions across 33 Microsoft Learn modules** — Azure Databricks architecture, Unity
  Catalog governance, compute selection, Lakehouse Federation, Delta Lake, Lakeflow Jobs,
  Structured Streaming and more.
- **Full rationales** — each question has a *Justification* plus an itemised
  *Why the other options are incorrect* list.
- **Answer keys are shuffled** — the correct answer is spread evenly over A/B/C/D
  (19/19/19/18) so position is never a hint.
- **Print / Save as PDF** — a dedicated print stylesheet strips the navigation and keeps each
  question card on one page, so the whole bank can be printed as a revision booklet.
- **Bilingual, browser-detected** — the site follows `navigator.languages` and serves French
  or Portuguese automatically, with a manual switcher that remembers the choice.

## How language selection works

The logic lives in a small inline script at the bottom of each page and needs no server:

1. A `?lang=fr` or `?lang=pt` query parameter forces the language and stores it in
   `localStorage`.
2. With no stored preference, `navigator.languages` is inspected: a language starting with
   `pt` opens the Portuguese page, `fr` (or anything else) opens the French page.
3. Clicking the **Français / Português** switcher stores the choice, so it wins over the
   browser language on later visits.

Both pages also declare `hreflang` alternates for search engines. If `localStorage` is
unavailable, detection still works and the site falls back to French for unknown languages.

## Repository structure

```
.
├── index.html     # French version (default page, served at the site root)
├── pt.html        # Brazilian Portuguese version
├── README.md      # this file
└── .nojekyll      # serve the files verbatim, bypassing Jekyll
```

Both pages are plain, dependency-free HTML with inline CSS and JavaScript — no build step,
no framework, no CDN, no fonts to download. `pt.html` is generated from `index.html` so the
two versions share an identical structure and stylesheet; only the text differs.

## Running locally

Open `index.html` directly in a browser, or serve the folder:

```bash
python -m http.server 8000
# then visit http://localhost:8000/
```

> The language auto-detection reads `navigator.languages`. To preview the Portuguese page
> from a French browser, open `pt.html` directly or append `?lang=pt`.

## Deployment

The site is published with **GitHub Pages** from the `main` branch, at the repository root:

```bash
gh api -X POST repos/eliswilliam/dp750-azure-databricks-exam/pages \
  -f "source[branch]=main" -f "source[path]=/"
```

Every push to `main` republishes the site. No workflow or build job is involved.

## Content notes

- The question bank is study material assembled from public Microsoft Learn DP-750 learning
  paths; the module tag on each card names the topic it maps to.
- Microsoft Learn module names are kept in English in both language versions, since they are
  the official names of the modules they reference.
- Some questions intentionally list only a reason for the options that are genuinely
  plausible distractors; those cards do not cover all three wrong options.

## Additional practice resources

Third-party question banks, listed here for extra drilling alongside this one:

- [ExamTopics — DP-750 practice questions](https://www.examtopics.com/exams/microsoft/dp-750/view/)
- [EduDump — DP-750 exam questions](https://www.edudump.com/exams/Microsoft/DP-750/view/)

These are community-run sites with their own content and accuracy, unconnected to this
project and to Microsoft.

## Disclaimer

This is an independent study aid. It is **not** affiliated with, endorsed by, or sponsored by
Microsoft or Databricks. Exam names and product names are trademarks of their respective
owners. Always check the official skills-measured document before sitting the exam.
