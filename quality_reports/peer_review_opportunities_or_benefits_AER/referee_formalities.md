# Referee C (Formalities) -- Notation Audit Report

**Date:** 2026-05-27
**Focus:** Notation, formulas, subscripts, equation-text correspondence

---

## Summary

| Type | HIGH | MEDIUM | LOW | Total |
|---|---|---|---|---|
| SUBSCRIPT_INCONSISTENCY | 3 | 1 | 0 | 4 |
| EQUATION_TEXT_MISMATCH | 1 | 0 | 1 | 2 |
| NOTATION_DRIFT | 1 | 3 | 3 | 7 |
| UNIT_MISMATCH | 0 | 0 | 1 | 1 |
| AMBIGUITY | 0 | 1 | 3 | 4 |
| MATHEMATICAL_ERROR | 0 | 0 | 1 | 1 |
| **Total** | **5** | **5** | **9** | **19** |

---

## Central Problem

Two parallel subscript conventions coexist and are never reconciled:

1. **Compact convention** (Equations 1, 2, 4; identification discussion): subscript-zero without individual indexing — `$d_0, t_0$`
2. **Fully explicit convention** (Equation 3; specification text): superscript-zero with individual indexing — `$d^0(i), m^0(i)$`

The most consequential instance: Equation 3 → Equation 4 changes **six notation elements simultaneously** (subscript convention, individual indexing, FE period-specificity, outcome district subscript, controls coefficient letter, error subscript) even though the only substantive change is adding an interaction term.

Secondary issue: `$t^0(i)$` (introduced as "time of protection"), `$m^0(i)$` ("calendar month of protection"), and `$t_0$` (from Equations 1-2) appear to be three symbols for the same concept.

---

## HIGH-severity findings (5)

### F1: IVUR subscripts differ between definition (Eq. 1) and usage (Eq. 3)
- **File:** 3_data.tex:26 vs 4_method.tex:24
- **Eq. 1:** `$IVUR_{d_0, t_0}$` — **Eq. 3:** `$IVUR_{d^0(i), m^0(i)}$`
- Two conventions for the same quantity: subscript vs superscript zero, `$t_0$` vs `$m^0(i)$`

### F2: Two symbols introduced for the same concept (time of protection)
- **File:** 4_method.tex:16
- `$t^0(i)$` ("time of protection") and `$m^0(i)$` ("calendar month of protection") both introduced; `$t^0(i)$` never used in any equation

### F3: Subscript convention changes between Eq. 1 and Eq. 3
- **File:** 3_data.tex:26 vs 4_method.tex:24
- District: `$d_0$` → `$d^0(i)$`; Time: `$t_0$` → `$m^0(i)$`

### F5: Equation 4 reverts to compact convention, changing 6 elements vs Eq. 3
- **File:** 5_results.tex:116-117
- Subscripts revert to `$d_0, t_0$`; FEs lose period subscript; outcome drops `$d(t)$`; `$\Gamma_t$` → `$\Delta_t$`
- A reader comparing Eq. 3 and Eq. 4 would conclude the model changed, not just the interaction

### F6: Equation 4 FEs appear non-period-specific, contradicting table notes
- **File:** 5_results.tex:117 vs 143
- Eq. 4 writes `$\gamma_{t_0} + \delta_g + \eta_{d_0}$` (simple FEs); table notes say "full set of arrival-group, year-month, and district-of-protection fixed effects" (period-specific)

---

## MEDIUM-severity findings (5)

### F4: IPBL subscript order changes between Eq. 2 and Eq. 3
- Eq. 2: `$f, p, s_0, t_0$` — Eq. 3: `$p(i), f(i), s^0(i), m^0(i)$`

### F7: Identification text uses simplified FE notation vs Eq. 3
- 4_method.tex:79 writes `$\eta_{d_0}$` and `$\gamma_{t_0}$` — Eq. 3 has `$\eta_{d^0(i),t}$` and `$\gamma_{m^0(i),t}$`

### F8: Arrival-group FE in identification text omits period subscript
- 4_method.tex:37 writes `$\delta_g$` — Eq. 3 has `$\delta_{g(i),t}$`

### F9: Summation index `$t$` in Eq. 1 collides with outcome-period `$t$`
- 3_data.tex:26 — suggest using `$\tau$` or `$k$` for the summation

### F13: Controls coefficient letter changes between Eq. 3 and Eq. 4
- Eq. 3: `$\Gamma_t$` — Eq. 4: `$\Delta_t$`

---

## LOW-severity findings (9)

- **F10:** `$PB$` in Eq. 2 never defined in text
- **F11:** Intro appropriately omits subscripts (no issue)
- **F12:** `$12^th$` renders "th" in math italic — use `$12^{\text{th}}$`
- **F14:** Outcome in Eq. 4 drops current-district subscript `$d(t)$`
- **F15:** "€1,000 increase in IPBL" = "one-unit increase" — could clarify
- **F16:** State subscript `$s^0(i)$` is used consistently (no issue)
- **F17:** Table 2 note "multiplied by 1000" could be clearer about scale interpretation
- **F18:** IPBL SD reported as 316.9 (euros) alongside standard shift of 0.3 (€1,000 units) — mixed scales
- **F19:** Colon before Eq. 4 promises immediate equation but paragraph intervenes
- **F20:** "first three months following protection" includes month 0 (protection month itself) — clarify "starting from"

---

## Notation Consistency Table

| Variable | Eq. 1 | Eq. 2 | Eq. 3 | Eq. 4 | ID text |
|---|---|---|---|---|---|
| District (initial) | `$d_0$` | — | `$d^0(i)$` | `$d_0$` | `$d_0$` |
| Time of protection | `$t_0$` | `$t_0$` | `$m^0(i)$` | `$t_0$` | `$t_0$` |
| State (initial) | — | `$s_0$` | `$s^0(i)$` | `$s_0$` | `$s^0(i)$` |
| Protection type | — | `$p$` | `$p(i)$` | `$p$` | `$p(i)$` |
| Family status | — | `$f$` | `$f(i)$` | `$f$` | `$f(i)$` |
| Arrival group | — | — | `$g(i)$` | `$g$` | `$g$` |
| FE: month-year | — | — | `$\gamma_{m^0(i),t}$` | `$\gamma_{t_0}$` | `$\gamma_{t_0}$` |
| FE: arrival group | — | — | `$\delta_{g(i),t}$` | `$\delta_g$` | `$\delta_g$` |
| FE: district | — | — | `$\eta_{d^0(i),t}$` | `$\eta_{d_0}$` | `$\eta_{d_0}$` |
| Controls coeff | — | — | `$\Gamma_t$` | `$\Delta_t$` | — |
| Outcome | — | — | `$Y_{id(t)t}$` | `$Y_{i,t}$` | — |
| Error | — | — | `$\epsilon_{id(t)t}$` | `$\epsilon_{i,t}$` | — |

---

## Recommendation

A single harmonization pass:
1. Choose one subscript convention for initial conditions (recommend: subscript-zero without $(i)$ everywhere, with a note that all initial-condition variables are individual-specific)
2. Choose one symbol for "month/time of protection" (recommend: `$t_0$`)
3. Make Equation 4 notationally identical to Equation 3 except for the interaction term
4. Use `$\Gamma_t$` in both equations
