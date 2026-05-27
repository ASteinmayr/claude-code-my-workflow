# CLAUDE.MD -- Academic Project Development with Claude Code

<!-- HOW TO USE: Replace [BRACKETED PLACEHOLDERS] with your project info.
     Customize Beamer environments and CSS classes for your theme.
     Keep this file under ~150 lines — Claude loads it every session.
     See the guide at docs/workflow-guide.html for full documentation. -->

**Project:** Opportunities or Benefits — Local Conditions and Refugee Labor Market Integration
**Institution:** University of Innsbruck
**Field:** Labor / migration economics
**Branch:** main

**Primary artifacts:** research papers (LaTeX), Beamer + Quarto slides, R-based data analysis / replication, research design (lit review, ideation, preregistration).

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- compile/render and confirm output at the end of every task
- **Single source of truth** -- Beamer `.tex` is authoritative; Quarto `.qmd` derives from it
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to [MEMORY.md](MEMORY.md)

Cross-session context lives in [MEMORY.md](MEMORY.md); past plans, specs, and session logs are in [quality_reports/](quality_reports/).

---

## Folder Structure

```
[YOUR-PROJECT]/
├── CLAUDE.MD                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Bibliography_base.bib        # Centralized bibliography
├── Figures/                     # Figures and images
├── Preambles/header.tex         # LaTeX headers
├── Slides/                      # Beamer .tex files
├── Quarto/                      # RevealJS .qmd files + theme
├── docs/                        # GitHub Pages (auto-generated)
├── scripts/                     # Utility scripts + R code
├── quality_reports/             # Plans, session logs, merge reports, decision records
├── explorations/                # Research sandbox (see rules)
├── templates/                   # Session log, quality report templates
└── master_supporting_docs/      # Papers and existing slides
```

---

## Commands

```bash
# LaTeX (3-pass, XeLaTeX only)
cd Slides && TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
BIBINPUTS=..:$BIBINPUTS bibtex file
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode file.tex

# Deploy Quarto to GitHub Pages
./scripts/sync_to_docs.sh LectureN

# Quality score
python scripts/quality_score.py Quarto/file.qmd

# Palette sync (LaTeX ↔ SCSS)
./scripts/check-palette-sync.sh

# Surface-count sync (README ↔ CLAUDE.md ↔ guide ↔ landing page)
./scripts/check-surface-sync.sh
```

**Palette contract:** color names in `Preambles/header.tex` must match SCSS variables in `Quarto/theme-template.scss`. See [`Preambles/README.md`](Preambles/README.md).

---

## Quality Thresholds (advisory)

| Score | Checkpoint | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for deployment |
| 95 | Excellence | Aspirational |

Enforced by `/commit` (halts + asks for override); not enforced by a git pre-commit hook.

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/compile-latex [file]` | 3-pass XeLaTeX + bibtex |
| `/deploy [LectureN]` | Render Quarto + sync to docs/ |
| `/extract-tikz [LectureN]` | TikZ → PDF → SVG |
| `/new-diagram [snippet] [output.tex]` | Scaffold a TikZ diagram from the gallery with prevention + review |
| `/proofread [file]` | Grammar/typo/overflow review |
| `/visual-audit [file]` | Slide layout audit |
| `/pedagogy-review [file]` | Narrative, notation, pacing review |
| `/review-r [file]` | R code quality review |
| `/qa-quarto [LectureN]` | Adversarial Quarto vs Beamer QA |
| `/slide-excellence [file]` | Combined multi-agent review |
| `/translate-to-quarto [file]` | Beamer → Quarto translation |
| `/validate-bib` | Cross-reference citations |
| `/devils-advocate` | Challenge slide design |
| `/create-lecture` | Full lecture creation |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/lit-review [topic]` | Literature search + synthesis |
| `/research-ideation [topic]` | Research questions + strategies |
| `/interview-me [topic]` | Interactive research interview |
| `/review-paper [file]` | Manuscript review (single-pass / `--adversarial` / `--peer <journal>` simulated pipeline) |
| `/respond-to-referees [report] [manuscript]` | R&R cross-reference + response draft |
| `/data-analysis [dataset]` | End-to-end R analysis |
| `/audit-reproducibility [paper]` | Enforce replication tolerance thresholds on paper ↔ code |
| `/learn [skill-name]` | Extract discovery into persistent skill |
| `/context-status` | Show session health + context usage |
| `/deep-audit` | Repository-wide consistency audit |
| `/permission-check` | Diagnose permission layers when prompts fire unexpectedly |
| `/seven-pass-review` | Seven-pass adversarial manuscript review (parallel forked subagents) |
| `/verify-claims [file]` | Chain-of-Verification fact-check (forked verifier, fresh context) |
| `/checkpoint [topic]` | Save a structured state snapshot (active plan, decisions, file pointers, next actions) before stopping or handing off |
| `/preregister [--style osf|aspredicted|aea-rct]` | Draft a preregistration document (OSF / AsPredicted / AEA RCT Registry) from a research spec |

---

<!-- CUSTOMIZE: Replace placeholder rows ([your-env], [.your-class]) with your own.
     Delete the rows marked "(example — delete)" once you've added yours. -->

## Beamer Custom Environments

| Environment | Effect | Use Case |
| --- | --- | --- |
| `[your-env]` | [Description] | [When to use] |
| `keybox` | Gold background box | Key points *(example — delete)* |
| `definitionbox[Title]` | Blue-bordered titled box | Formal definitions *(example — delete)* |

## Quarto CSS Classes

| Class | Effect | Use Case |
| --- | --- | --- |
| `[.your-class]` | [Description] | [When to use] |
| `.smaller` | 85% font | Dense content *(example — delete)* |
| `.positive` | Green bold | Good annotations *(example — delete)* |

---

## Current Project State

*No lecture decks yet.* HelloWorld stubs deleted 2026-05-18 after toolchain verification — XeLaTeX confirmed via 4-page Beamer compile of the (now-deleted) HelloWorld stub via the updated `/compile-latex` skill; Quarto 1.9.37 confirmed via `quarto --version`. When the first lecture lands, add a row table here: `| Lecture | Beamer (.tex) | Quarto (.qmd) | Key content |`.

### Paper Drafts

| Paper | Status | Folder |
| --- | --- | --- |
| Opportunities or Benefits? Local Conditions and Refugee Labor Market Integration | Drafting | [articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/](articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/) |

---

## Local Toolchain (set up 2026-05-18)

| Tool | Status | Notes |
| --- | --- | --- |
| XeLaTeX (TeX Live 2025) | ✓ | Beamer + paper compilation works |
| R 4.6.0 | ✓ | `/data-analysis`, `/review-r` work |
| Python 3.11 | ✓ | Internal scripts work |
| git | ✓ | Version control works |
| Quarto 1.9.37 | ✓ | `/deploy`, `/qa-quarto`, `/translate-to-quarto` work |
| gh CLI 2.92.0 | ✓ | Run `gh auth login` once to authorize PR access |
| pdf2svg | ⚠ not yet checked | Needed for `/extract-tikz`. Install: `brew install pdf2svg` |

Run `./scripts/validate-setup.sh` to re-check after installs.

### Bibliography Arrangement

`Bibliography_base.bib` is a **symlink** to `articles/Opportunities_or_Benefits.../bib_andreas.bib`. Per INV-5 (single bibliography), this is the canonical source — Beamer and Quarto both resolve citations through `Bibliography_base.bib`. The article folder owns the actual file. If the article folder is later removed or renamed, the symlink breaks; restore by re-pointing the symlink or by replacing it with a real file.

### Working Preferences (locked in 2026-05-18)

- **R paths:** plain relative (`../data/...`); no `here::here()`
- **Seed:** `set.seed(83)` once at top of every script
- **Tolerances:** point estimates 1e-4, SEs 1e-3; **strict near-miss policy**
- **Effort default:** medium (`/effort high` for paper-revision and submission-ready work)
- **Reporting:** concise bullets; details on request
- **Palette:** deferred — Emory blue/gold defaults retained until first slide is built
- **Domain-reviewer customization:** deferred — `/slide-excellence` will warn until lenses are field-tuned

Full details in [`.claude/WORKFLOW_QUICK_REF.md`](.claude/WORKFLOW_QUICK_REF.md).
