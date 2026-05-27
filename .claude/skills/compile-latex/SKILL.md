---
name: compile-latex
description: Compile a LaTeX document (Beamer slides OR research articles) with XeLaTeX (3–4 passes + bibtex). Auto-detects `\documentclass{beamer}` vs. anything else and adjusts the build context — Beamer slides compile from `Slides/` with shared `Preambles/` + repo-root bibliography; articles compile from their own folder (e.g. `articles/<name>/`) with local preamble + local bibliography. Use when user says "compile", "build the slides", "build the paper", "rebuild the PDF", "run latex", "render the tex", or asks why a `.tex` file isn't producing a PDF.
argument-hint: "[basename OR path to .tex file — `.tex` extension optional]"
allowed-tools: ["Read", "Bash", "Glob", "Grep"]
---

# Compile LaTeX Documents

Compile a LaTeX document using XeLaTeX with full citation resolution. Auto-detects whether the target is a Beamer deck or a non-Beamer document (`extarticle`, `article`, `report`, `scrartcl`, …) and adjusts the build context accordingly.

## Step 1: Parse `$ARGUMENTS` and resolve the target

`$ARGUMENTS` may be:

- A bare basename (`HelloWorld`) — assume Beamer convention; file is at `Slides/<basename>.tex`
- A basename with extension (`HelloWorld.tex`) — same as above, with `.tex` stripped
- A repo-relative path (`articles/foo/0_master.tex` or `articles/foo/0_master`) — use the path as-is, strip trailing `.tex` if present
- An absolute path — use it directly

Defensive parsing:

1. If `$ARGUMENTS` ends with `.tex`, strip the extension.
2. If the stripped arg contains a `/`, treat it as a path (relative or absolute). The basename is the last segment; the parent dir is everything before.
3. Otherwise, treat the arg as a bare basename and look at `Slides/<arg>.tex`.
4. Verify the file exists. If not, use `Glob` (`**/<basename>.tex`) to find candidates and stop with a clear error if there's no match or multiple matches.

## Step 2: Detect documentclass

`Grep` for `\documentclass` in the resolved file (first 20 lines is enough). Match the class name inside the braces.

- Class is `beamer` → **Beamer mode** (Step 3a).
- Anything else (`article`, `extarticle`, `report`, `scrartcl`, …) → **Article mode** (Step 3b).

If you can't find a `\documentclass` line, stop and report — the file is probably an `\input` fragment, not a master file.

## Step 3a: Beamer mode

Beamer decks in this repo follow a fixed convention: `Slides/<basename>.tex` `\input`s `header.tex` from `Preambles/`, and citations resolve against `Bibliography_base.bib` at the repo root.

```bash
cd Slides
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode <basename>.tex
BIBINPUTS=..:$BIBINPUTS bibtex <basename>
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode <basename>.tex
TEXINPUTS=../Preambles:$TEXINPUTS xelatex -interaction=nonstopmode <basename>.tex
```

`<basename>` is the file stem without `.tex` (e.g. `HelloWorld`, not `HelloWorld.tex`). Note that `bibtex` takes the stem (no extension); `xelatex` takes the filename with `.tex`.

## Step 3b: Article mode

Research articles in `articles/<name>/` are self-contained: their `0_master.tex` (or equivalent) carries its own inline preamble and the `.bib` files live in the same folder. No env overrides needed.

```bash
cd <parent-dir>
xelatex -interaction=nonstopmode <basename>.tex
bibtex <basename>
xelatex -interaction=nonstopmode <basename>.tex
xelatex -interaction=nonstopmode <basename>.tex
```

`<parent-dir>` is the directory of the resolved file from Step 1 (use the absolute path to avoid cwd-loss issues across Bash invocations).

If a 3rd-pass `.log` still shows `Label(s) may have changed. Rerun to get cross-references right.`, run a 4th `xelatex` pass.

### Handling missing LaTeX packages

When `xelatex` reports `File '<pkg>.sty' not found`, install the missing package from the frozen TeX Live archive matching the local install. As of 2026-05, `tlmgr` defaults to the TL 2026 remote, but TinyTeX installs are commonly still on TL 2025 — installs against the wrong year fail with "Local TeX Live is older than remote repository."

```bash
tlmgr --repository https://ftp.math.utah.edu/pub/tex/historic/systems/texlive/2025/tlnet-final install <pkg>
```

For TinyTeX users compiling a paper with many packages, batch install them in one call. Common omissions for empirical-econ articles: `extsizes`, `threeparttable`, `tabularray` (which itself needs `ninecolors`), `pgfplots`, `mhchem`, `siunitx`, `morefloats`, `rotfloat`, `adjustbox`, `dcolumn`, `paralist`, `tabulary`, `makecell`.

## Step 4: Check for warnings

After the final pass, summarize the build:

```bash
echo "Missing chars: $(grep -c 'Missing character' <basename>.log)"
echo "Overfull: $(grep -c 'Overfull' <basename>.log)"
echo "Undefined refs/citations: $(grep -c 'undefined' <basename>.log)"
echo "Font shape warnings: $(grep -c 'Font shape.*undefined' <basename>.log)"
echo "BibTeX warnings: $(grep -c 'Warning--' <basename>.blg)"
echo "PDF size + pages: $(ls -la <basename>.pdf | awk '{print $5}') bytes; $(grep -E 'Output written.*pages' <basename>.log | tail -1)"
```

Report each count. A clean build is all zeros (except PDF size + pages).

## Step 5: Open the PDF (optional)

On macOS, `open <basename>.pdf`. On Linux, `xdg-open <basename>.pdf`. Skip if running in a non-GUI session.

## Step 6: Report results

Concise summary:

- Mode: Beamer or article
- PDF page count
- Per-warning-type counts from Step 4
- Compilation success or specific failure

If any per-warning counts are non-zero, surface the first few examples (use `grep -A 2 "Overfull" <basename>.log | head -10` etc.) so the user knows where to look.

## Why 3 (or 4) passes?

1. First `xelatex` → `.aux` with citation keys
2. `bibtex` → `.bbl` with formatted references
3. Second `xelatex` → incorporates bibliography
4. Third `xelatex` → resolves cross-references with final page numbers
5. Fourth `xelatex` (sometimes) → needed when `\ref{}` / `\pageref{}` moved citations across a page break in pass 3

If the 3rd-pass log still has "Label(s) may have changed. Rerun to get cross-references right.", run a 4th pass.

## Important

- **Always use XeLaTeX**, never pdflatex. Several packages and native Unicode font handling depend on XeTeX.
- **Beamer mode env vars are critical**: `TEXINPUTS=../Preambles` (so `\input{header}` resolves), `BIBINPUTS=..` (so the repo's `Bibliography_base.bib` symlink resolves).
- **Article mode env vars are NOT needed**: articles are self-contained.
- **`bibtex` argument has no extension**; `xelatex` argument has `.tex`. Don't double-extension (`file.tex.tex`).
- **Bash `cd` persistence is not 100% reliable across multiple `Bash` tool invocations.** Either chain all xelatex/bibtex commands inside a single `Bash` call after `cd`, or re-issue `cd <absolute path>` at the start of each.
