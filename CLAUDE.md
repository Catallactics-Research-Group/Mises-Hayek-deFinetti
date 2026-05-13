# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repository is

This is a **research and writing repository**, not a software project. It supports an interdisciplinary paper, *Bayesians in the Catallaxy* synthesizing three literatures: Austrian catallactics (Mises/Hayek), Bruno de Finetti's operational subjective probability, and modern arbitrage-based finance. The eventual artifact is a manuscript; most files are Quarto (`.qmd`) or Markdown source plus rendered PDFs and a BibTeX bibliography.

The `pyproject.toml` / `uv.lock` are inherited from a project template and are not actively used — there is no Python code path to build or test. Treat the repo as documents-first.

## Directory layout

The repo is organized into one draft directory plus three topical lanes, with supporting directories around them. Choose by **what the content is**, not who wrote it:

- `draft/` — the manuscript-in-progress. Currently `proposal-short.qmd` (the JEP-targeted version) plus `rae_intro.md`. The biblio (`biblio.bib`) lives here alongside the prose.
- `philosophical/` — lane for the philosophical groundwork of arbitrage trinitarianism. Holds `brittany-michael-brief.qmd` (collaborator brief for Brittany Oakes & Michael Otteson) and any prose/notes that develop that lane.
- `mathematical/` — lane for the mathematical foundations (operational subjective probability on Misesian microfoundations). Holds `erin-emmy-brief.qmd` (brief for Erin Beckman & Emmy Heywood).
- `computational/` — lane for computational statistical catallactics (agent-based economics on Mises-Hayek-de Finetti microfoundations). Holds `jake-marc-brief.qmd` (brief for Jake Gunther & Marc Dotson).
- `project_meta/` — shared scope, outline (`Outline.qmd`), timeline. Affects everyone; changes here warrant a PR.
- `sources/` — bibliography (`biblio.bib`, `bibliography.bib`) and reading notes. No draft prose.
- `working_notes/` — personal scratch space. `author_<name>/` folders (`author_tjb`, `author_emmy`, `author_marc`) hold rough notes not yet routed into a lane or the draft.
- `appendices/` — formal derivations and extended technical material too detailed for the main text.
- `archive/` — superseded material (notably `legacy_structure/` — the original template's `code/data/figures/writing/` scaffold, plus older proposal drafts `proposal_old.qmd` and `proposal_full.qmd`). Prefer archiving over deleting.

Three additional top-level directories (`presentations/`, `tools/`, `writing/`) exist
from earlier project state and are not part of the draft+lanes structure; treat them
as auxiliary until reorganized.

Content matures by moving — a note in `working_notes/author_tjb/` may be promoted into
`philosophical/` once it has shape, and prose from a lane may be promoted into `draft/`
once it's ready for the manuscript.

## Quarto rendering

Each subdirectory with renderable content has its own `Makefile`. There is no
top-level build. Two patterns recur:

- `draft/Makefile` — `make pdf` / `make html` / `make all` / `make clean` for `proposal-short.qmd`. Uses `quarto render --to <fmt>`.
- `philosophical/Makefile`, `mathematical/Makefile`, `computational/Makefile`, `sources/readings-guide/Makefile` — `make render` produces both PDF and GFM `.md` per `.qmd` (the lane Makefiles glob `*.qmd` so new lane documents are picked up automatically).

Important: a bare `quarto render <file>.qmd` honors all `format:` entries in the file's
YAML frontmatter and emits every format at once. Format-specific targets in the Makefiles
exist for when you only need one. `make clean` removes generated artifacts; `.quarto/` is
gitignored.

To render an ad-hoc `.qmd` outside these Makefile-managed directories, use `quarto render
<path>.qmd` (optionally `--to pdf|html|gfm`) from that file's directory so relative
bibliography paths resolve.

## Bibliography

`biblio.bib` lives in `draft/` and `sources/` (and `working_notes/author_tjb/`).
`sources/bibliography.bib` is a separate, larger file. When citing in a `.qmd`, the
`bibliography:` YAML key (or the directory's `_quarto.yml`) points to the copy that lives
alongside the source file. If you add citations, update the bib file that the document
actually references rather than assuming a single canonical bibliography.

## Editing norms

From `CONTRIBUTING.md`:
- Free to edit directly: `working_notes/`, `sources/source_notes/`, the three lane directories (`philosophical/`, `mathematical/`, `computational/`).
- Use a pull request for: `project_meta/` and `draft/`.
- Quoting sources: include page numbers when possible.
- When in doubt where something belongs, default to `working_notes/`.

## Subject-matter shorthand

When reading or editing prose, these terms recur and carry technical meaning specific to
this project's synthesis:

- **Triad Arbitrage** — the central thesis: arbitrage is the unifying principle across all three pillars (catallactics, de Finetti, finance).
- **Catallactics** — Austrian conception of the market as an entrepreneurial discovery process (Mises, Hayek, Kirzner).
- **DBA / Dutch Book Argument** — de Finetti's derivation of probability axioms from coherent betting (no-arbitrage at the individual agent level).
- **Fundamental Theorem of Prevision ≡ Fundamental Theorem of Asset Pricing** — a load-bearing equivalence the paper develops (Nau 1999, 2001, 2023).
- **Computational statistical catallactics** — the project's proposed methodology, agent-based and grounded in the three pillars.

`project_meta/Outline.qmd` is the current section plan; `draft/proposal-short.qmd`
is the JEP-targeted prose version of the same argument.
