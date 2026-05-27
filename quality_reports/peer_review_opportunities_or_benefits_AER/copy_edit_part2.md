# Copy Editor Report — Part 2: Mechanisms through Appendix

**Date:** 2026-05-27
**Files:** 5a_mechanisms.tex, 6_robustness.tex, 7_discussion.tex, 8_conclusion.tex, appendix.tex

---

## Summary

| Category | High | Medium | Low | Total |
|---|---|---|---|---|
| SPELLING | 2 | 1 | 3 | 6 |
| GRAMMAR | 2 | 4 | 1 | 7 |
| READABILITY | 1 | 6 | 0 | 7 |
| STRUCTURE | 0 | 3 | 2 | 5 |
| STYLE | 0 | 3 | 5 | 8 |
| PUNCTUATION | 1 | 2 | 2 | 5 |
| **Total** | **6** | **19** | **13** | **38** |

---

## HIGH-severity (6)

### Issue 1: Subject-verb agreement
- **File:** 5a_mechanisms.tex:3
- **Current:** "whether a particular type of occupations drive the $IVUR$ results"
- **Fix:** "whether particular types of occupations drive the $IVUR$ results"

### Issue 2: Sentence fragments
- **File:** 5a_mechanisms.tex:3
- **Current:** "First, by desired occupations, which are usually registered by the caseworkers at the PES for each job-seeker. And second, by seasonal and non-seasonal jobs."
- **Fix:** "First, we disaggregate by desired occupations, which are usually registered by caseworkers at the PES for each job seeker, and second, by seasonal and non-seasonal jobs."

### Issue 25: Potentially reversed logic about benefits and accommodation
- **File:** 7_discussion.tex:12
- **Current:** "the prospect of lower benefits if they consider moving to private accommodation makes staying in the state less appealing"
- **Issue:** Sentence structure implies lower benefits apply when moving to private accommodation, which would make moving less appealing — opposite of intended meaning.
- **Fix:** "although the reduced benefit levels may still affect their decision-making if they consider transitioning to private accommodation"

### Issue 35: Missing period
- **File:** appendix.tex:293
- **Current:** "This change happens within four months of receiving protection"
- **Fix:** "This change happens within four months of receiving protection."

### Issue 36: Typo "Conventions refugees"
- **File:** appendix.tex:312
- **Current:** "Conventions refugees"
- **Fix:** "Convention refugees"

### Issue 44: Figure note describes wrong FE specification
- **File:** appendix.tex:181
- **Current:** Figure note for year-and-month-FE robustness says "year-month...fixed effects" (joint)
- **Issue:** This robustness check uses *separate* year and month FEs — the note should say so
- **Fix:** "arrival-group, year, month, and district-of-protection fixed effects"

---

## MEDIUM-severity (19)

| # | File:Line | Category | Issue | Fix |
|---|-----------|----------|-------|-----|
| 3 | 5a_mech:4 | PUNCT | Spurious comma before "that" | Remove comma |
| 6 | 5a_mech:11 | READ | "all other but the desired occupations" | "all occupations other than the desired ones" |
| 8 | 5a_mech:62 | READ | ~45-word sentence with nested clauses | Split into two sentences |
| 9 | 5a_mech:62 | GRAM | \citet singular/plural agreement | Verify author count for each citation |
| 12 | 5a_mech:71 | STYLE | "bad control" informal for AER | Quote term or rephrase |
| 15 | 5a_mech:62 | READ | "additionally" redundant with "jointly" | Drop "additionally" |
| 17 | 6_rob:4 | READ | Ambiguous "data covers refugees up until" | Rewrite: "covers refugees who received protection up to August 2023" |
| 20 | 6_rob:15 | READ | ~55-word sentence on clustering | Split at colon |
| 21 | 6_rob:15 | READ | Wild bootstrap sentence at upper limit | Split after "confidence intervals widen" |
| 27 | 7_disc:14 | STRUCT | Policy Simulation uses \textbf not \subsection* | Use \subsection*{Policy Simulation} |
| 28 | 7_disc:17 | STYLE | IPBL not in math mode | $IPBL$ |
| 31 | 8_conc:14 | READ | "In turn" implies causation where there is none | "At the same time" |
| 32 | 8_conc:19 | READ | "remaining without employment instead of moving and being unemployed" confusing | Rewrite with clearer contrast |
| 33 | 8_conc:19 | GRAM | "resembling the findings of work-first policies" | "consistent with findings on work-first policies" |
| 37 | app:327 | SPELL | "Lower-Austria" vs "Lower Austria" | Remove hyphen |
| 38 | app:324 | GRAM | "Based on the Table A5" | "Based on Table A5" |
| 39 | app:324 | GRAM | "happened since 2016" | "occurred from 2016 onward" |
| 40 | app:329 | PUNCT | Spurious comma before "got" | Remove comma |
| 45 | app:270 | GRAM | "welfare system is subject to federal states" | "administered by the federal states" |
| 46 | app:274 | STYLE | "The Austrian welfare system knows" (Germanism) | "includes" |
| 50 | app:238 | STRUCT | >200-word paragraph mixing IVUR and IPBL discussion | Split after IVUR discussion |
| 51 | app:240 | READ | Dense clause on family benefits coefficient | Split into two sentences |

---

## LOW-severity (13)

- Issue 4: "job-seeker" vs "job seeker" inconsistency
- Issue 5: "$IVURs$" — plural "s" in math mode
- Issue 7: "left figure" should be "left panel"
- Issue 10: No change needed (i.e. punctuation correct)
- Issue 11: "upward-biased" → "upward biased" after predicate
- Issue 13: Filler "It is important to note that" → trim
- Issue 14: "district-fixed effects" → "district fixed effects"
- Issue 16: Tense inconsistency "limited...have been observed"
- Issue 18: Comma before "for whom" — rewrite with "restrict to"
- Issue 19: "Also" at sentence start → "This modification likewise"
- Issue 22: Trailing whitespace
- Issue 23: "month-year-fixed effects" → "year-month fixed effects"
- Issue 29: IPBL in text mode in table note
- Issue 34: Conclusion paragraph structure (optional split)
- Issue 42: Inconsistent heading capitalization in appendix
- Issue 43: Missing comma after "In Tyrol and Vienna"
- Issue 47: "Those also partly differ" → "These measures also differ across states"
- Issue 48: "110 Euros" → "€110"
- Issue 52: Heading hierarchy inconsistency between parallel appendix sections
