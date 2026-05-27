# Bibliography Semantic Audit

**Date:** 2026-05-18
**Bibliography:** `articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/bib_andreas.bib` (72 entries) — also reachable via the `Bibliography_base.bib` symlink at the repo root
**Files scanned:** 26 `.tex` files under `articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/` (master + 9 section files + `appendix.tex` + 15 files in `tables/`)
**Scope note:** the shipped `/validate-bib` skill defaults to `Slides/`, `Quarto/`, `guide/`, `master_supporting_docs/`. Scope was widened to the article folder for this run.

## Summary

| Check | Critical | Medium | Low | Info |
|---|---|---|---|---|
| Structural — missing citation keys | 0 | — | — | — |
| Structural — unused entries | — | — | — | 38 |
| Structural — typo candidates | — | — | 0 | — |
| Semantic — DOI duplicates | 3 | — | — | — |
| Semantic — title duplicates | 9 | — | — | — |
| Semantic — author+year+journal duplicates | — | 9 | — | — |
| Semantic — title Jaccard soft duplicates | — | — | 3 | — |
| Style consistency | — | — | 2 files | — |
| DOI verification (offline) | — | — | — | 43 entries have DOIs; not network-verified |

**One-line verdict:** the bibliography is functionally correct (all 34 cited keys resolve, no typos), but contains 9 confirmed paper-level duplicates and 4 Zotero junk entries — the technical debt of merging 3 source files. None of this affects the compile, but consolidation would shrink the bib from 72 → ~59 entries and remove genuine ambiguity for any future referee or collaborator reading the source.

## Critical Issues

### Hard duplicates (same DOI — same paper, two entries)

| Keys | DOI | Cited? | Recommended canonical |
|---|---|---|---|
| `bratsberg_immigrant_2020` / `Bratsberg2020ImmigrantGenerosity` | 10.1016/j.labeco.2020.101854 | Neither cited | Drop both, OR keep `bratsberg_immigrant_2020` (Zotero-style) |
| `chiswick_effect_1978` / `chiswick_effect_1978-1` | 10.1086/260717 | Neither cited | Drop both, OR keep `chiswick_effect_1978` |
| `black_does_2003` / `black_does_2003-1` | 10.1016/s0047-2727(02)00014-2 | Neither cited | Drop both, OR keep `black_does_2003` |

### Title duplicates (same normalized title, different keys — same paper)

| Keys | Title (truncated) | Cited? | Recommended canonical |
|---|---|---|---|
| `azlor2020` / `azlor_local_2020` | "Local labour demand and immigrant employment" | `azlor_local_2020` cited 2x | Keep `azlor_local_2020`; drop `azlor2020` |
| `barsbai2024` / `barsbai_immigrating_2023` | "Immigrating into a recession: Evidence from family migrants to the U.S." | `barsbai2024` cited 1x | Keep `barsbai2024`; drop `barsbai_immigrating_2023` |
| `borjas2001` / `borjas_does_2001` | "Does immigration grease the wheels of the labor market" | `borjas2001` cited 1x | Keep `borjas2001`; drop `borjas_does_2001` |
| `brell2020` / `brell_labor_2020` | "Labor market integration of refugee migrants in high-income countries" | `brell_labor_2020` cited 1x | Keep `brell_labor_2020`; drop `brell2020` |
| `dustmann2024` / `dustmann_refugee_2023` | "Refugee benefit cuts" | `dustmann2024` cited 4x | Keep `dustmann2024`; drop `dustmann_refugee_2023`. **Year discrepancy: one entry says 2024, other says 2023** — likely a working-paper-vs-published mismatch; verify the canonical year. |
| `ferwerda2023` / `ferwerda_immigrants_2023` | "Do immigrants move to welfare? Subnational evidence from Switzerland" | `ferwerda2023` cited 2x | Keep `ferwerda2023`; drop `ferwerda_immigrants_2023` |
| `bratsberg_immigrant_2020` / `Bratsberg2020ImmigrantGenerosity` | "Immigrant responses to social insurance generosity" | Neither cited | (also flagged above by DOI) |
| `chiswick_effect_1978` / `chiswick_effect_1978-1` | "Effect of Americanization on the earnings of foreign-born men" | Neither cited | (also flagged above by DOI) |
| `black_does_2003` / `black_does_2003-1` | "Does the availability of high-wage jobs for low-skilled men affect welfare expenditures?" | Neither cited | (also flagged above by DOI) |

**Net effect of consolidation:** 9 duplicate pairs → 9 canonical entries (drop 9). Plus optionally drop both keys of each uncited pair (drop 6 more). Total reduction: 9–15 entries.

## Medium-severity Issues

### Author+Year+Journal duplicates (likely same paper)

All 9 of these overlap with the Critical title-duplicate findings above — same diagnoses, different signal. The Degenhardt and Foged pairs flagged by author+year are **intentional** (different papers by the same author in the same year):

- `degenhardt2025` (gig-economy paper, Degenhardt & Nimczik) ≠ `degenhardt2025initial` (initial low-barrier employment, Degenhardt sole-author, arXiv 2512.17422)
- `foged_integrating_2022` ≠ `foged_comparing_2022` (different Foged papers)

## Low-severity Issues

### Soft title duplicates (Jaccard 0.7–1.0, not exact)

| Pair | Jaccard | Same paper? |
|---|---|---|
| `adema2025` ↔ `agersnap_welfare_2020` | 0.89 | **No.** Adema (2025) is a *Comment* on Agersnap-Jensen-Kleven (2020). High Jaccard because Adema's title is literally Agersnap's title + ": Comment". Keep both. |
| `borjas2001` ↔ `noauthor_project_nodate` | 0.75 | Yes — `noauthor_project_nodate` is a Project MUSE link to the same Borjas paper. Junk entry; drop. |
| `borjas_does_2001` ↔ `noauthor_project_nodate` | 0.75 | Same as above. |

### Mixed citation styles within a file

| File | Style breakdown | Concern |
|---|---|---|
| `1_intro.tex` | 18× `\citep` / 8× `\citet` / 6× `\cite` | Dominant style (`\citep` 56%) below the 80% threshold. `\cite` without a directional variant is generally discouraged — convert to `\citep` (parenthetical) or `\citet` (textual) for clarity. |
| `5_results.tex` | 3× `\cite` / 1× `\citep` / 1× `\citet` | Small sample (5 citations); low-priority. |

## Informational

### Unused entries (38 of 72 = 53%)

The merged bib is a working reference library, not a strictly-cited-set. About half of the entries aren't currently cited in this manuscript. This is normal for a research bib that the author maintains across multiple projects. No action required unless the goal is a strict submission-ready package — in which case prune to only-cited entries.

Unused entries (excluding the duplicates already flagged above): `Bratsberg2014ImmigrantsInsurance`, `ahrens_labor_2024`, `aigner2019`, `bahar2024`, `bailey_social_2022`, `bansak_improving_2018`, `beaman_social_2012`, `becker_consequences_2019`, `borjas_assimilation_1985`, `degenhardt2025` (the gig-economy paper), `degenhardt2025initial` (the arXiv paper just added — not yet cited; this is expected, the differentiation paragraph in §1 hasn't been written yet), `edin2004`, `edin_ethnic_2003`, `eurostat_2023`, `fasani_lift_2021`, `foged_access_2023`, `foged_comparing_2022`, `foged_integrating_2022`, `friesenecker_housing_2021`, `hoynes_local_2000`, `jaschke_scared_2022`, `kanas_greater_2023`, `rengs2017`, plus the 4 junk `noauthor_*_nodate` entries.

### Junk Zotero placeholder entries (4)

- `noauthor_global_nodate`
- `noauthor_impact_nodate`
- `noauthor_notitle_nodate`
- `noauthor_project_nodate` (duplicate of Borjas — flagged in soft-duplicates above)

These are Zotero "untitled / no metadata" exports. Drop all 4.

### DOI verification (skipped)

43 of 72 entries have DOIs. Network verification via crossref would catch "wrong DOI", "DOI assigned to a different paper", and similar errors. Skipped in this run (the user's session is not network-gated, but the skill default allows opt-in via the bare `--semantic` flag — I judged this overkill given the manuscript is mid-draft and the structural+duplicate findings dominate). Can be opted in later via a follow-on run.

## Next steps (in execution order)

1. **Drop 9 uncited duplicate-pair entries** (the "Recommended canonical" column above). Zero risk to the manuscript — all dropped entries have no citations.
2. **Drop the 4 `noauthor_*_nodate` Zotero junk entries.** Zero risk.
3. **Verify the `dustmann2024` year discrepancy** (one entry says 2024, the merged-in entry says 2023). Pick canonical year, keep the entry with correct metadata.
4. *(Optional)* **Standardize citation style in `1_intro.tex`** — convert the 6 `\cite{}` calls to either `\citep` or `\citet` depending on context.
5. *(Optional)* **Prune the remaining 24 unused-but-not-junk entries** if the goal is a submission-ready package. Defer if the bib is a working reference library.
6. *(Optional)* **Network DOI verification** for the 43 DOI-carrying entries — catches misattributed DOIs.

Step 1+2 are pure mechanical cleanup with zero risk to the manuscript. The bib goes from 72 → 59 entries, all functionally relevant.
