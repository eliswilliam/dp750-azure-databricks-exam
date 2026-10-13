# DP-750 Azure Databricks — Practice Exam Bank

A self-contained, printable study bank of **75 practice questions** for the Microsoft
**DP-750: Implementing Data Engineering Solutions Using Azure Databricks** exam.

Each question ships with the four answer options, the highlighted correct answer, a
justification, and a breakdown of why every other option is wrong — all cross-referenced
to the corresponding Microsoft Learn module. The bank is **interactive**: pick an option
and the correction appears immediately.

The document is available in **two languages**, French and Brazilian Portuguese, on a single
static site.

## Live site

| Language | URL |
| --- | --- |
| Français | https://eliswilliam.github.io/dp750-azure-databricks-exam/ |
| Português (BR) | https://eliswilliam.github.io/dp750-azure-databricks-exam/pt.html |

## Features

- **Answer and get corrected on the spot** — click a proposal and the page immediately marks
  your choice, highlights the correct option and unfolds the justification. A sticky bar
  tracks score, questions answered and success rate.
- **75 questions across 33 Microsoft Learn modules** — Azure Databricks architecture, Unity
  Catalog governance, compute selection, Lakehouse Federation, Delta Lake, Lakeflow Jobs,
  Structured Streaming and more.
- **Full rationales** — each question has a *Justification* plus an itemised
  *Why the other options are incorrect* list.
- **Answer keys are shuffled** — the correct answer is spread evenly over A/B/C/D
  (19/19/19/18) so position is never a hint.
- **Print / Save as PDF** — a dedicated print stylesheet strips the navigation and the quiz
  bar and keeps each question card on one page, so the whole bank can be printed as a
  revision booklet with every answer and explanation visible.
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

## Answering the questions

Answers are hidden on screen until you commit to one, so the bank can be used for real
practice rather than reading:

- **Click a proposal** (or focus it and press <kbd>Enter</kbd> / <kbd>Space</kbd>). Your choice
  turns red if it is wrong, the correct option is highlighted, and the justification plus the
  *why the other options are incorrect* list unfold.
- **The first click is final** for that question — the bar above the questions records it, so
  the score means something.
- **"Show all answers"** reveals every correction at once without touching the score, for
  when you just want to read through the bank.
- **"Reset"** clears the whole session and hides the answers again.

Nothing is stored or sent anywhere: progress lives in the page and resets on reload.

Without JavaScript the page degrades cleanly into the static answer key it was before — all
answers and explanations simply stay visible.

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
