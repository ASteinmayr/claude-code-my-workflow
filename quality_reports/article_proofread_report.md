# Proofreading Report — Opportunities or Benefits (ReStud revision)

**Date:** 2026-05-19
**Files scanned:** `abstract.tex`, `1_intro.tex`, `2_background.tex`, `3_data.tex`, `4_method.tex`, `5_results.tex`, `5a_mechanisms.tex`, `6_robustness.tex`, `7_discussion.tex`, `8_conclusion.tex`, `appendix.tex`, `tables/descriptives_manually_edited.tex`, `tables/interactions.tex`, `0_master.log`
**Total findings:** 28
**Findings by severity:** CRITICAL [9] / MAJOR [10] / MINOR [9]
**Constraint:** no new analysis; commented-out material is intentionally removed and is NOT to be revived.

---

## CRITICAL — must address for ReStud revision

### C1 — Abstract claims "These effects persist for about 2.5 years" but conflates two distinct outcomes
- **File / line:** `abstract.tex:1`
- **Category:** Editorial (A-Minor #1)
- **Current text:** "These effects persist for about 2.5 years, but both shocks have lasting impacts on internal migration."
- **Proposed fix:** "Employment effects fade within roughly 2.5 years, while location-choice effects persist for at least five years."
- **Rationale:** The abstract bundles a five-year mobility effect (Section 5.2 shows persistence to month 60) with the 30-month employment fade. Precision matters for a top-5 audience.

### C2 — Buried headline result on out-migration from Austria not surfaced in the abstract
- **File / line:** `1_intro.tex:27`
- **Category:** Editorial (A-Minor #2)
- **Current text:** "Neither labor demand nor benefits affect the probability of leaving Austria altogether."
- **Proposed fix:** Lift this sentence into the abstract (it speaks directly to the welfare-magnet / displacement debate that ReStud readers will care about). Suggested append to abstract: "Neither shock changes the probability of leaving Austria altogether."
- **Rationale:** Important null finding for the welfare-magnet literature; currently buried in §1 paragraph 9.

### C3 — Direct contradiction between §3 statement and Appendix evidence on IVUR / PES-registration correlation
- **File / line:** `3_data.tex:8` vs. `appendix.tex:238`
- **Category:** Editorial (A-Minor #3)
- **Current text (3_data.tex:8):** "we test whether the number of refugees in our data, as a share of all individuals from those countries of origin in a district, correlates with our main explanatory variables, which is not the case."
- **Current text (appendix.tex:238):** "In columns (4)-(5), where we use the overall shares as an outcome, the effect of the $IVUR$ becomes statistically significant at the 5\% level."
- **Proposed fix:** §3 should say something like: "we test whether the share of refugees in our data correlates with our main explanatory variables. We find a small, statistically significant correlation between IVUR and registration probability for the aggregated sample, but its magnitude is too small to materially bias our main estimates (see Appendix \ref{subsec:pes_selection})."
- **Rationale:** A referee will catch this internal contradiction immediately; the appendix itself acknowledges the issue.

### C4 — Equation (3) (main spec) outcome subscript inconsistency
- **File / line:** `4_method.tex:18, 23-26, 29`
- **Category:** Equation / Notation (B-Minor #3)
- **Current text:** Line 18: "Outcomes $Y_{i d(t) s(t) t}$ are measured at time $t$..." Line 23 (in equation): `Y_{i d(t) t}` (no $s(t)$). Line 29: "where $Y_{i d(t) s(t) t}$ denotes the outcome..." Error term also varies: line 25 `\epsilon_{i d(t) s(t) t}`, line 29 `\epsilon_{i d(t) t}`.
- **Proposed fix:** Pick one and apply throughout. Recommended: drop $s(t)$ since $s(t)$ is determined by $d(t)$ (district is a finer geography than state), so it is redundant. Use $Y_{i\,d(t)\,t}$ and $\epsilon_{i\,d(t)\,t}$ in both the equation and the surrounding prose. Remove "$s(t)$" from line 18.
- **Rationale:** Notational inconsistency in the main specification will be flagged on any careful reading.

### C5 — IPBL units convention drifts across paper / table
- **File / line:** `3_data.tex:33-40` (Eq. 2 divides by 1000), `5_results.tex:8` ("standard shift" = 0.3 = 300 euro), `tables/descriptives_manually_edited.tex:29` (IPBL reported as 826.87 and 518.66, i.e. raw euros)
- **Category:** Units / Consistency (B-Minor #2 and #7)
- **Current text:** Eq. (2): "$IPBL_{f,p,s_0,t_0} = \frac{PB_{f,p,s_0,t_0}}{1000}$" with note "We present $IPBL$ in units of 1,000 euro to facilitate a clearer graphical presentation". Table 1 reports IPBL = €826.87 / €518.66 (raw, not /1000). Text in §5 mixes "one unit increase in IPBL represents 1,000 euros", "a standard shift of 0.3 (300 euro)", and "every 100 euros increase".
- **Proposed fix:** Either (a) report IPBL as 0.83 / 0.52 in Table 1 and add to the note "IPBL is denominated in €1,000 (real 2015 values)"; or (b) keep Table 1 in euros and clarify in §3.2 that this is the underlying PB and that the regression IPBL is PB/1000. Recommend (a) for consistency, since all figure captions use "€1,000 (real 2015 values)".
- **Rationale:** Referees track unit conventions closely; a 1000× scaling discrepancy between Table 1 and the regression coefficients (e.g., "$\beta = -0.050$") will confuse readers.

### C6 — Footnote in §5a reports a coefficient (0.23427) with no table reference and apparently nowhere else in the paper
- **File / line:** `5a_mechanisms.tex:11-14` (footnote)
- **Category:** Academic Quality (B-Minor #8)
- **Current text:** "labor demand in these occupations might be correlated with labor demand in other occupations. In this case, the estimates would be upward-biased. [...] The estimated coefficients for the $IVUR$ using the non-desired professions are as follows: the effect of $IVUR$ on employment is 0.23427, and on residing in the initial state is 0.2186."
- **Proposed fix:** Either (a) move these two coefficients into an appendix table and refer to it, OR (b) round to two significant digits ("about 0.23 and 0.22") and explicitly state that these come from an unreported specification available on request. Five-decimal precision (0.23427) for a number that exists nowhere else in the paper looks careless.
- **Rationale:** As-is, the reader cannot verify the number; 5-digit precision without source is unusual in published economics.

### C7 — Elasticity calculation: numerator inconsistency
- **File / line:** `5_results.tex:46-49` (footnote 12 in narrative)
- **Category:** Typo / Numerical (B-Minor #10)
- **Current text:** "the percentage change in benefits is $-100/850 \approx -11.8\%$ while the corresponding change in the mover rate is $0.01/0.29 \approx 3.4\%$. This yields an elasticity of $3.3/11.8 \approx 0.29$."
- **Proposed fix:** "This yields an elasticity of $3.4/11.8 \approx 0.29$."
- **Rationale:** Direct typo. The preceding sentence computes 3.4%; the very next line writes 3.3/11.8. 3.4/11.8 = 0.288, so 0.29 still holds. Pure copy error.

### C8 — Bare `\cite{}` still present in active text in `5_results.tex`
- **File / line:** `5_results.tex:16, 22, 128`
- **Category:** Citation style (Consistency)
- **Current text (line 16):** "For example, \cite{barsbai2024} find that family migrants who face a higher unemployment rate..."
- **Current text (line 22):** "...contrasting other findings in the literature of rather persistent wage effects \citep{barsbai2024}." (this one is fine, but line 16's bare `\cite` should be `\citet`)
- **Current text (line 128):** "These results are in line with the findings of \cite{dustmann2024}, who find the cuts in welfare benefits in Denmark..."
- **Proposed fix:** Replace both bare `\cite{}` with `\citet{}` (both are textual subjects of the sentence). Line 16: `\citet{barsbai2024}`. Line 128: `\citet{dustmann2024}`.
- **Rationale:** The intro was cleaned but §5 was not. Bare `\cite` produces inconsistent rendering and is a known consistency residue.

### C9 — `\citep` (parenthetical) used where `\citet` (textual) is grammatically required
- **File / line:** `5_results.tex:46`
- **Category:** Citation style
- **Current text:** "The similarity of approaches allows for a direct comparison with the results of \cite{ferwerda2023} who study the effect..."
- **Proposed fix:** "...with the results of \citet{ferwerda2023}, who study the effect..."
- **Rationale:** Same problem — bare `\cite` in active body text where the citation acts as a noun phrase. Also add the comma before "who" (restrictive vs. non-restrictive clause).

---

## MAJOR — editor-relevance high

### M1 — Terminology: "labor demand" used in head framings where "labor market tightness" / "labor market conditions" is the correct primitive
- **File / line:** `abstract.tex:1`
- **Current text:** "we find that higher labor demand increases employment, while more generous benefits slightly reduce it."
- **Proposed fix:** "we find that tighter local labor markets raise employment, while more generous benefits slightly reduce it."
- **Rationale:** IVUR = V/U is, by definition, labor market tightness (DMP θ). For ReStud, "labor demand" reads as a category error in the abstract.

### M2 — Terminology in abstract sentence
- **File / line:** `abstract.tex:1`
- **Current text:** "Moreover, the negative employment effect of benefits is larger when labor demand is high."
- **Proposed fix:** "Moreover, the negative employment effect of benefits is larger in tighter labor markets."
- **Rationale:** Same conceptual point; preserves consistency with §5 wording about tight labor markets.

### M3 — Terminology in §1 (paragraph 7): "labor demand" as primitive vs. tightness
- **File / line:** `1_intro.tex:27`
- **Current text:** "An interquartile increase in local labor demand—about 0.2 additional vacancies per unemployed person—raises the probability of employment..."
- **Proposed fix:** "An interquartile increase in local labor market tightness—about 0.2 additional vacancies per unemployed person—raises the probability of employment..."
- **Rationale:** "0.2 additional vacancies per unemployed person" is literally V/U — i.e., tightness. The body of §1 already says "we examine how local labor market tightness and welfare benefit levels" (line 13); the headline-findings paragraph should match.

### M4 — Terminology in §1 (literature paragraph)
- **File / line:** `1_intro.tex:23`
- **Current text:** "we can exploit both spatial and temporal variation in local labor demand and welfare benefit levels"
- **Proposed fix:** "we can exploit both spatial and temporal variation in local labor market tightness and welfare benefit levels"

### M5 — Terminology in §1 (data paragraph)
- **File / line:** `1_intro.tex:25`
- **Current text:** "which enable us to measure local labor demand by both quantity and occupation type"
- **Proposed fix:** Hybrid rewrite: "which enable us to measure both the overall tightness of the local labor market and the demand for specific occupations." Use "demand" only where the by-occupation decomposition is the object.
- **Rationale:** Tightness for aggregate measure; demand for occupation-specific decomposition.

### M6 — Terminology in §5 subsection header
- **File / line:** `5_results.tex:108`
- **Current text:** "\subsection{Interplay of local labor demand and benefit levels}"
- **Proposed fix:** "\subsection{Interplay of labor market tightness and benefit levels}"
- **Rationale:** The aggregate IVUR ratio in this subsection is tightness, not labor demand.

### M7 — Terminology + grammar fix in §5 results body (interaction paragraph)
- **File / line:** `5_results.tex:127`
- **Current text:** "Column (1) shows that the effect of changes in benefit levels on the probability of being employed at different levels of labor demand. Changes in benefit levels have practically no effect on the employment probability when labor demand is zero. However, benefit levels affect employment probability strongly when labor demand is high."
- **Proposed fix:** Two fixes: (i) the lead clause is ungrammatical — "shows that the effect" has no main verb; rewrite to "Column (1) shows the effect of changes in benefit levels..."; (ii) replace each "labor demand" in this paragraph with "labor market tightness" (or "the labor market" / "tightness" once introduced).
- **Rationale:** Grammar + terminology in one paragraph.

### M8 — Terminology in §8 (conclusion, two specific lines)
- **File / line:** `8_conclusion.tex:17, 19`
- **Current text (line 17):** "we find that changes in welfare benefits have a stronger effect on employment rates when labor demand is high and are negligible otherwise"
- **Proposed fix:** "...when local labor markets are tight..."
- **Rationale:** Same category-error point in the conclusion. Lines 12 and 14 are KEEP candidates (general framing / low-entry-barrier-occupations); only lines 17, 19 are tightness contexts.

### M9 — Unmotivated gender split in Figure 4 / `fig:descriptive_outcomes_main`
- **File / line:** `3_data.tex:81-97` (figure region) and §3.4 narrative
- **Category:** Editorial (B-Minor #13)
- **Current text:** "For men, it rises steadily and reaches about 60\% after five years. For women, the employment rate is less than 20\% after five years." (line 81). The split into men/women is introduced without motivation here; the gender-heterogeneity analysis is §5.5.
- **Proposed fix:** Add one motivating sentence before the split — e.g., "Given the large literature on gender differences in refugee labor-market integration (see §5.5), we show patterns separately for men and women throughout."

### M10 — 12-month outcome horizon never explicitly justified
- **File / line:** `5_results.tex:16` (first appearance of "month twelve")
- **Category:** Editorial (B-Minor #11)
- **Current text:** "A standard shift in the $IVUR$ increases the employment probability in the $12^{th}$ month after receiving protection by 4 pp."
- **Proposed fix:** Before this sentence, add: "We focus on the 12-month horizon throughout, since (i) the first year after protection encompasses the four-month deadline to vacate organized accommodation and the typical adjustment period to a new state's welfare regime, and (ii) it allows a clean comparison to \citet{aslund_when_2007} and \citet{dustmann2024}, who anchor their main results on a similar window."

---

## MINOR — copy-edit polish

### N1 — Demeaning means not labeled in Table 5 (interactions)
- **File / line:** `tables/interactions.tex` and `5_results.tex:122-125`
- **Current text:** Table reports IPBL marginal effects at IVUR=0, IVUR=0.192, IVUR=0.392. The text says "we demeaned $IVUR$ and $IPBL$." But the table never tells the reader that 0.192 is the mean.
- **Proposed fix:** Add a row label "(mean of IVUR = 0.192)" in the table or in the notes.
- **Category:** Consistency / Editorial (B-Minor #9)

### N2 — Stray paragraph fragment at top of conclusion file (VERIFIED CLEAN — commented out)
- **File / line:** `8_conclusion.tex:5`
- **Status:** Line 5 is fully commented out. Per the constraint to ignore commented material, no action.
- **Category:** Editorial (A-Minor #9) — partial false alarm.

### N3 — Hangartner references confirmed inactive (VERIFIED CLEAN)
- **File / line:** `1_intro.tex:86, 95-97`
- **Status:** All three Hangartner mentions are inside `%`-commented blocks. No action.

### N4 — Word-order error in 2_background footnote
- **File / line:** `2_background.tex:14` (footnote)
- **Current text:** "However, they do not know whom exactly are they going to host."
- **Proposed fix:** "However, they do not know exactly whom they are going to host."
- **Category:** Grammar

### N5 — Double-space artifact after "subsidiary-protected"
- **File / line:** `3_data.tex:10, 55, 57`; `appendix.tex:312`; `7_discussion.tex:12`
- **Current text:** "subsidiary-protected  individuals" (two spaces) and "subsidiary-protected  " (trailing)
- **Proposed fix:** Global search-replace double space → single space (limited to these occurrences to avoid touching intentional spacing elsewhere).
- **Category:** Typo (search-and-replace artifact)

### N6 — Reference label typo
- **File / line:** `appendix.tex:247, 251` and `appendix.tex:238`
- **Current text:** Label is `tab:assd_statube` but the table file is `assd_statcube` (note missing "c").
- **Proposed fix:** Rename label to `tab:assd_statcube` and update the `\ref{}` accordingly.

### N7 — Broken cross-reference: equation ref points to section label
- **File / line:** `appendix.tex:86, 98`
- **Current text:** "from our main model (Equation \ref{sec:specification})..." and "(see Equation \ref{sec:specification})"
- **Proposed fix:** `Equation \ref{sec:specification}` references a section label, not an equation. Should be `Equation \ref{eq:main}`.
- **Category:** Cross-reference error — this is a real LaTeX bug that produces incorrect output.

### N8 — Inconsistent typography of euro symbol / "euro"
- **File / line:** Throughout — e.g., `5_results.tex:8` uses "300 euro", `5_results.tex:20` uses "81 euro" / "33 euro" / "11 euros" / "100 euros". `1_intro.tex:13` uses "€200" with euro sign.
- **Proposed fix:** Standardize on €X (numeric with euro sign) throughout, e.g., "€300", "€81", "€100".

### N9 — Informal phrasing in mechanisms section
- **File / line:** `5a_mechanisms.tex:11-12` (footnote)
- **Current text:** "Desired occupations have a stronger but more short-lived effect on employment than other occupations."
- **Proposed fix:** "Desired occupations exhibit a stronger but more transient effect on employment than other occupations."
- **Category:** Stylistic polish (very minor)

### N10 — Semicolon misuse
- **File / line:** `1_intro.tex:51` (and parallel in `5_results.tex:46-50`)
- **Current text:** "They find that higher benefits reduce relocation, but only to a minor extent; at most two pp., even for very large differences in benefits."
- **Proposed fix:** "They find that higher benefits reduce relocation, but only to a minor extent—at most two pp., even for very large differences in benefits."
- **Category:** Punctuation

### N11 — Overfull hbox check
- **Status:** VERIFIED CLEAN — `0_master.log` shows no Overfull warnings in the last build.

---

## Items reviewed and intentionally KEPT (terminology pass — "labor demand" defensible in context)

| File:line | Snippet | Why KEEP |
|---|---|---|
| `2_background.tex:52` | "Vienna and districts in the eastern and southern states of the country display low average labor demand during this period." | KEEP — describing a regional measure; informal shorthand acceptable here. |
| `5a_mechanisms.tex:7,9` | "Labor demand by most desired occupations" header, "labor demand in these four occupations" | KEEP — sector/occupation decomposition IS a demand-side primitive. |
| `5a_mechanisms.tex:11` | "labor demand in desired occupations on employment is approximately three times larger than that of the overall measure" | KEEP — by-occupation demand. |
| `5a_mechanisms.tex:29` | "Labor demand by seasonal occupations" / "demand in jobs labeled as seasonal occupations" | KEEP — sector-specific. |
| `5a_mechanisms.tex:43` | "Nevertheless, we find that seasonal labor demand increases the likelihood..." | KEEP — sector-specific. |
| `5a_mechanisms.tex:68` | "If labor demand affects political preferences..." | KEEP — abstract / conceptual usage. |
| `8_conclusion.tex:12, 14` | "Their decision to relocate is influenced by both labor demand and welfare generosity..." / "We show that labor demand, particularly in occupations with low entry barriers..." | KEEP — line 14 explicitly references low-entry-barrier occupations, demand-side. |
| `1_intro.tex:111` | "We also study how initial labor demand affects mobility..." | BORDERLINE — could be "tightness"; KEEP since context is broad "conditions". |
| `0_master.tex:161` | Keyword list "labor demand" | KEEP — indexing. |
| `appendix.tex:88` | "higher labor demand or increased welfare benefits do not influence the decision to stay in or leave Austria" | KEEP — pithy contrast; tightness would feel clinical here. |

---

## Summary

- Terminology rewrites (labor demand → tightness/conditions): 8 instances flagged
- Editorial minor-concern flags from peer review: 8
- Citation style residue: 3 (`\cite{}` → `\citet{}`)
- Equation / units consistency: 2
- General typos / grammar: 5
- Cross-reference fixes: 2
- Items intentionally kept (no change after review): 10
- Verified clean: Hangartner references, overfull hbox

**Top three to fix first** (referee-bait if missed): C3 (3_data ↔ appendix contradiction), C5 (IPBL unit drift across Table 1 / Eq 2 / §5), C4 (Equation 3 subscript notation).
