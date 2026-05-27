# Copy Editor Report — Part 1: Abstract through Results

**Date:** 2026-05-27
**Files:** abstract.tex, 1_intro.tex, 2_background.tex, 3_data.tex, 4_method.tex, 5_results.tex

---

## Summary

| Category | High | Medium | Low | Total |
|----------|------|--------|-----|-------|
| SPELLING | 0 | 0 | 1 | 1 |
| GRAMMAR | 2 | 12 | 14 | 28 |
| READABILITY | 11 | 18 | 3 | 32 |
| STRUCTURE | 0 | 2 | 0 | 2 |
| STYLE | 0 | 3 | 14 | 17 |
| PUNCTUATION | 0 | 1 | 5 | 6 |
| **Total** | **13** | **36** | **37** | **86** |

## Key Patterns

1. **Broken parallel constructions** ("not only...but also") appear at least 3 times
2. **Dangling modifiers** ("Unlike related studies...we"; "Similar to this study, we"; "contrasting other findings...we")
3. **Excessive hedging** ("does not seem to," "can barely be influenced by," "is likely due to a situation where")
4. **Filler phrases** ("This question has received considerable attention," "In other words," "It is important to note")
5. **Overly long sentences** (40+ words) concentrated in data and methods sections

---

## HIGH-severity findings (13)

### Finding 4 (1_intro.tex:11): Unbalanced "not only...but also"
- **Current:** "not only to foster integration but also to shape migration flows, manage fiscal resources, and sustain public support"
- **Fix:** "to foster integration, shape migration flows, manage fiscal resources, and sustain public support"

### Finding 6 (1_intro.tex:11): Three consecutive vague-abstraction sentences
- **Current:** "Yet integration outcomes also depend... Ultimately, successful integration hinges... Understanding these responses..."
- **Fix:** Consolidate to two sentences, cutting "Ultimately, successful integration hinges..."

### Finding 7 (1_intro.tex:13): Two sentences say the same thing at different specificity
- **Current:** "We study how refugees adjust their labor supply... Specifically, we examine how local labor market tightness..."
- **Fix:** Merge into one sentence

### Finding 10 (1_intro.tex:17): Structurally broken sentence
- **Current:** "A decrease in monthly benefits increases the propensity to relocate and male employment temporarily and female employment more persistently."
- **Fix:** "A decrease in monthly benefits increases the propensity to relocate, raises male employment temporarily, and raises female employment more persistently."

### Finding 17 (1_intro.tex:27): Mixing levels and changes
- **Current:** "lower benefit levels have modest effects: a reduction of €100 increases employment"
- **Fix:** "benefit reductions have modest effects: a €100 decrease increases employment"

### Finding 20 (1_intro.tex:45): Throat-clearing opening
- **Current:** "The question of how immigrants choose a location has received extensive attention in the literature"
- **Fix:** "How immigrants choose where to settle is well studied, but..."

### Finding 28 (1_intro.tex:51): Stock filler sentence
- **Current:** "This question has received considerable attention."
- **Fix:** Delete entirely

### Finding 33 (1_intro.tex:108): Long footnote runs ~50 words covering two claims
- **Fix:** Split into two sentences

### Finding 35 (1_intro.tex:108): Hard-to-parse prepositional stacking
- **Current:** "in the district and time of receiving unrestricted labor market access instead of at arrival"
- **Fix:** "in the district of residence at the time of receiving unrestricted labor market access, rather than at arrival"

### Finding 53 (2_background.tex:10): 43-word sentence with nested acronyms
- **Current:** "the Federal Office for Immigration and Asylum (Bundesamt für Fremdenwesen und Asyl, or BFA), an authority directly subordinate to..."
- **Fix:** "The Federal Office for Immigration and Asylum (BFA) processes all first-instance asylum applications."

### Finding 67 (3_data.tex:8): "encompassing" appears twice in three sentences
- **Fix:** Rewrite to eliminate repetition and reduce data-dictionary style

### Finding 76 (3_data.tex:40): 42-word sentence defining IPBL
- **Fix:** Split into two sentences: definition + conditioning variables

### Finding 79 (3_data.tex:47): ~80-word sentence with 4 outcomes and 3 footnotes
- **Fix:** Use enumerated list: "(a) employment, (b) marginal employment, (c) earnings, (d) log wages"

---

## MEDIUM-severity findings (36)

The full report contains 36 MEDIUM findings. Key clusters:

**Introduction (13 findings):** Dangling modifiers (F15, F46), hedging language (F24, F27), broken parallel constructions (F36, F37), unclear referents (F40, F45), imprecise framing (F16, F18, F29, F32, F43)

**Background (6 findings):** Institutional jargon unexplained for AER audience (F52, F54, F55), choppy three-sentence sequence (F62), vague characterizations (F64, F66)

**Data (6 findings):** Long sentences with ambiguous referents (F68, F69, F70, F72, F84), "logged" vs "log" (F80)

**Methods (5 findings):** Garden-path second identification question (F94), "are allowed to vary by" (F96), 43-word nested prepositional phrases (F97), redundant "time-constant with constant effects" (F103)

**Results (6 findings):** Awkward "maintaining steady" (F105), confusing "a shift roughly amounting to" (F106), unnecessary "we observe that" (F115), stacked adjectives (F116), misattributed agency (F125, F126)

---

## LOW-severity findings (37)

Mostly: filler phrases to cut ("Taken together," "Moreover...also," "In other words"), informal verbs ("see" → "find," "utilize" → "use"), minor punctuation (Oxford comma, trailing spaces, "Wald-Tests" → "Wald tests"), and style nits.
