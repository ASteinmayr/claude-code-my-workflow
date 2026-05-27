# Workflow Quick Reference

**Model:** Contractor (you direct, Claude orchestrates)

---

## The Loop

```
Your instruction
    ↓
[PLAN] (if multi-file or unclear) → Show plan → Your approval
    ↓
[EXECUTE] Implement, verify, done
    ↓
[REPORT] Summary + what's ready
    ↓
Repeat
```

---

## I Ask You When

- **Design forks:** "Option A (fast) vs. Option B (robust). Which?"
- **Code ambiguity:** "Spec unclear on X. Assume Y?"
- **Replication edge case:** "Just missed tolerance. Investigate?"
- **Scope question:** "Also refactor Y while here, or focus on X?"

---

## I Just Execute When

- Code fix is obvious (bug, pattern application)
- Verification (tolerance checks, tests, compilation)
- Documentation (logs, commits)
- Plotting (per established standards)
- Deployment (after you approve, I ship automatically)

---

## Quality Gates (No Exceptions)

| Score | Action |
|-------|--------|
| >= 80 | Ready to commit |
| < 80  | Fix blocking issues |

---

## Non-Negotiables

- **R paths:** plain relative paths (`../data/raw/file.csv`, `../scripts/R/02_clean.R`). No `here::here()`, no absolute paths. Scripts must be runnable from `scripts/R/`.
- **R seeds:** `set.seed(83)` exactly once at the top of every script using randomness; never inside loops or functions (INV-9).
- **R figures:** transparent background, explicit width/height, custom `theme_custom()` on every committed ggplot (INV-11/12). Theme function definition deferred — fill in when first figure script is written.
- **R numerics:** no float equality, CDF clamping with `eps = 1e-12`, integer literals for counts. See `r-code-conventions.md` §8.
- **Replication tolerance:** point estimates `1e-4`, standard errors `1e-3`. **Strict near-miss policy** — any result within 10% of tolerance is flagged for investigation, not silently accepted.
- **LaTeX/Beamer:** XeLaTeX 3-pass via `/compile-latex`; no `\pause` / overlays (INV-6); max 2 colored boxes per slide (INV-7).
- **Beamer ↔ Quarto:** Beamer is authoritative; sync to Quarto in the same task; notation identical (INV-2).
- **Palette:** LaTeX + SCSS must agree (INV-1). Verify with `./scripts/check-palette-sync.sh`.
- **Bibliography:** one canonical file `Bibliography_base.bib` (INV-5).

---

## Preferences

**Visual:** transparent ggplot backgrounds; institutional palette in figures and slides; `theme_custom()` to be defined when first figure script lands.
**Reporting:** **concise bullets; details on request.** Quote line numbers when referencing code.
**Session logs:** post-plan, incremental, end-of-session — in `quality_reports/session_logs/`.
**Replication:** **strict** — flag near-misses for investigation, never silently accept.
**Effort:** **medium by default.** Override per-task: `/effort high` for paper-revision and submission-ready work, `/effort low` for routine renders and smoke tests.

---

## Exploration Mode

For experimental work, use the **Fast-Track** workflow:
- Work in `explorations/` folder
- 60/100 quality threshold (vs. 80/100 for production)
- No plan needed — just a research value check (2 min)
- See `.claude/rules/exploration-fast-track.md`

---

## Next Step

You provide task → I plan (if needed) → Your approval → Execute → Done.
