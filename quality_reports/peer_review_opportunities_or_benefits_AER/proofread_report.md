# Proofreading Report: Opportunities or Benefits

**Date:** 2026-05-27
**Standard:** AER submission-ready
**Files reviewed:** abstract.tex, 1_intro.tex, 2_background.tex, 3_data.tex, 4_method.tex, 5_results.tex, 5a_mechanisms.tex, 6_robustness.tex, 7_discussion.tex, 8_conclusion.tex, appendix.tex

---

## Summary

| Category | High | Medium | Low | Total |
|----------|------|--------|-----|-------|
| GRAMMAR | 1 | 3 | 1 | 5 |
| TYPO | 2 | 0 | 3 | 5 |
| CONSISTENCY | 0 | 6 | 5 | 11 |
| ACADEMIC | 0 | 3 | 0 | 3 |
| LATEX | 0 | 2 | 25+ | 27+ |
| **Total** | **3** | **14** | **34+** | **51+** |

---

## HIGH-severity issues (3)

### Issue 13: Subject-verb disagreement
- **File:** 3_data.tex:55
- **Current:** "A substantial portion, 59.6\%, exhibit limited German language proficiency"
- **Proposed:** "A substantial portion, 59.6\%, exhibits limited German language proficiency"
- **Category:** GRAMMAR

### Issue 43: Missing period at end of sentence
- **File:** appendix.tex:293
- **Current:** "This change happens within four months of receiving protection"
- **Proposed:** "This change happens within four months of receiving protection."
- **Category:** TYPO

### Issue 46: "Conventions refugees" typo
- **File:** appendix.tex:312
- **Current:** "Conventions refugees are entitled to minimum income support"
- **Proposed:** "Convention refugees are entitled to minimum income support"
- **Category:** TYPO

---

## MEDIUM-severity issues (14)

### Issue 1: Roadmap omits the Discussion section
- **File:** 1_intro.tex:185
- **Current:** "Section \ref{sec:results} presents the results, and Section \ref{sec:conclusion} concludes."
- **Proposed:** "Section \ref{sec:results} presents the results, Section \ref{sec:discussion} discusses additional considerations and policy simulations, and Section \ref{sec:conclusion} concludes."

### Issue 2: Awkward opening sentence
- **File:** 1_intro.tex:108
- **Current:** "complement active literature on initial conditions' (long-term) effects for refugees"
- **Proposed:** "complement an active literature on the (long-term) effects of initial conditions for refugees"

### Issue 7: "However" opens new subsection without antecedent
- **File:** 2_background.tex:26
- **Current:** "However, there are differences in the type and extent of benefits they receive."
- **Proposed:** "There are, however, differences in the type and extent of benefits Convention refugees and subsidiary-protected individuals receive."

### Issue 14/15: Ordinal "th" renders in math italic
- **File:** 3_data.tex:57 (and line 75)
- **Current:** `$12^{th}$`
- **Proposed:** `$12^{\text{th}}$` or `12\textsuperscript{th}`

### Issue 29: Interaction intuition paragraph appears before its equation
- **File:** 5_results.tex:112-113
- **Current:** "A negative cross-partial..." paragraph appears before Equation \ref{eq:main_interaction}
- **Proposed:** Move paragraph to after the equation (after line 119)

### Issue 32: IVUR/IPBL missing math-mode in table caption
- **File:** 5_results.tex:182
- **Current:** "Effects of IVUR and IPBL at Approval"
- **Proposed:** "Effects of $IVUR$ and $IPBL$ at Approval"

### Issue 34: Spurious comma before restrictive "that"
- **File:** 5a_mechanisms.tex:4
- **Current:** "we explore the concern, that the benefit cuts"
- **Proposed:** "we explore the concern that the benefit cuts"

### Issue 36: Spurious comma before "for whom"
- **File:** 6_robustness.tex:7
- **Current:** "we only consider refugees, for whom we can determine"
- **Proposed:** "we only consider refugees for whom we can determine"

### Issue 44: IVUR/IPBL use \textit in appendix instead of $...$
- **File:** appendix.tex:229, 235
- **Current:** `\textit{IVUR}` and `\textit{IPBL}`
- **Proposed:** `$IVUR$` and `$IPBL$`

### Issue 45: Caption missing IVUR/IPBL formatting
- **File:** appendix.tex:121
- **Current:** "Effect of the IVUR and IPBL on selected outcomes"
- **Proposed:** "Effect of the $IVUR$ and $IPBL$ on selected outcomes"

### Issue 47: Unnecessary article before table reference
- **File:** appendix.tex:324
- **Current:** "Based on the Table A5 of their working paper"
- **Proposed:** "Based on Table A5 of their working paper"

### Issue 48: Inconsistent Euro formatting
- **File:** appendix.tex:296
- **Current:** "if the income exceeds 110 Euros"
- **Proposed:** "if the income exceeds €110"

### Issue 52: Systematic missing ~ before \ref throughout manuscript
- **File:** All files
- **Current:** "Figure \ref", "Table \ref", "Section \ref", etc. without non-breaking tildes
- **Proposed:** Systematically add ~ before all \ref commands

### Issue 53: Inconsistent IVUR/IPBL formatting across contexts
- **File:** Multiple files
- **Current:** Body uses `$IVUR$`, headings use `\textit{IVUR}`, appendix uses `\textit{IVUR}`, some captions use plain `IVUR`
- **Proposed:** Standardize to `$IVUR$` in body and captions, `\textit{IVUR}` only in headings

---

## LOW-severity issues (34+)

Mostly non-breaking spaces before \ref commands (25+ instances across all files), plus:
- Issue 3/4: Inconsistent quotation mark conventions (1_intro.tex)
- Issue 16: Inconsistent dash style in footnote (3_data.tex:55)
- Issue 17: Dangling preposition (3_data.tex:57)
- Issue 18: "logged" vs "log" inconsistency (3_data.tex:47)
- Issue 25-27: Double spaces (5_results.tex:44, 47, 157)
- Issue 33: Inconsistent capitalization in table caption (5_results.tex:182)
- Issue 39: Inconsistent dash style (7_discussion.tex:21)
- Issue 40: \textbf used instead of \subsection* for "Policy Simulation" (7_discussion.tex:14)
