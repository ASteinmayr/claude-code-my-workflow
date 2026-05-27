# Methods Referee Report

**Calibrated to:** American Economic Review (AER)
**Disposition:** CREDIBILITY
**Paper type:** Reduced-form
**Critical peeve:** Insists on correct standard-error clustering for the unit of treatment.
**Constructive peeve:** Appreciates when the paper anticipates the obvious referee objections.
**Date:** 2026-05-27

---

## Executive Verdict

**Score:** 68
**Recommendation:** Major Revision
**Headline:** The IVUR identification is credible and well-executed; the IPBL identification rests on a weaker foundation that the paper acknowledges but does not adequately bound, and the clustering choice does not match the treatment-variation level for either treatment, which is a first-order inference concern.

---

## One-Paragraph Summary (Methods Focus)

The paper estimates the causal effect of two initial conditions -- local labor market tightness (IVUR, measured at the district-month level) and welfare benefit generosity (IPBL, measured at the state-protection-type-family-status-month level) -- on refugees' employment, mobility, and welfare receipt over a 60-month post-protection window. Identification rests on a dispersal-based quasi-random assignment of asylum-seekers to districts within arrival-group cells (gender x quarter x initial-state x family-status), combined with district and month-year-of-protection fixed effects. The authors estimate OLS regressions separately for each outcome-month, with period-specific fixed effects. The balance table (Table 1) supports quasi-random assignment within cells. The IVUR identification is strong: district FE absorb permanent tightness differences, and the remaining within-district month-to-month variation is plausibly exogenous to individual refugee characteristics. The IPBL identification is weaker: variation comes primarily from a small number of state-level reforms (3 states, 2015-2017), and the authors themselves note the reforms may proxy for broader anti-refugee sentiment. Standard errors are clustered at the state-year-of-protection level, which is a deliberate but non-standard choice that does not align with the treatment-variation level for either IVUR (district-month) or IPBL (state-protection-type-family-status-month). The paper commendably reports wild-cluster bootstrap CIs given Austria's nine states and explicitly acknowledges that IPBL employment effects weaken under the bootstrap. Robustness checks are extensive and well-targeted, though several key threats are not addressed.

---

## Pre-Scoring Sanity Checks

| Check | PASS/FAIL | Evidence |
|---|---|---|
| **Sign check** | PASS | IVUR positive on employment, IPBL negative on employment -- both consistent with standard labor supply theory. |
| **Magnitude check** | PASS | A 0.2-unit IVUR shift raises 12-month employment by 4 pp off an 11.3% base (35% increase) -- large but plausible given near-zero starting employment. A €300 IPBL shift reduces employment by 1.5 pp (13%) -- modest and reasonable. |
| **Dynamics check** | PASS (partial) | Effects materialize immediately and fade by 30 months -- consistent with the "immediate constraints" narrative. However, there are no formal pre-trends shown in the compiled paper. |
| **Clustering check** | **FAIL** | See MC1 below. Standard errors are clustered at state x year-of-protection, but IVUR varies at district x month and IPBL varies at state x protection-type x family-status x month. |
| **Sample check** | PASS | Sample construction is documented; attrition test in Appendix A shows no treatment-related selection. |

**One FAIL (Clustering) caps the composite score at 70.**

---

## Dimension Scores

| # | Dimension | Weight | Score | Weighted |
|---|---|---|---|---|
| 1 | Identification | 40% | 68 | 27.2 |
| 2 | Estimation | 25% | 75 | 18.75 |
| 3 | Inference (SEs, clustering, MHT) | 20% | 50 | 10.0 |
| 4 | Robustness | 10% | 72 | 7.2 |
| 5 | Replication | 5% | N/A (no code in repo) | 0.0 |
| | **Composite** | | | **63.2 (adjusted to 68 for disclosure quality)** |

Note: I add 5 points for the paper's unusually transparent discussion of the clustering issue (including explicit wild-cluster bootstrap with Webb weights and candid acknowledgment that IPBL employment effects approach zero under the bootstrap).

---

## Major Concerns

### MC1: Standard-error clustering does not match the treatment-variation level for either treatment

**Dimension:** #3 (Inference)
**Severity:** MAJOR

**Description.** The paper clusters standard errors at the state x year-of-protection level (approximately 9 states x 8 years = ~72 clusters). The IVUR varies at the district x month level (approximately 80 districts x 90+ months), and IPBL varies at the state x protection-type x family-status x month level (roughly 9 x 2 x 2 x 90). The Moulton (1990) problem cuts in opposite directions for the two treatments: for IVUR, clustering at the state-year level is *too coarse* (it over-corrects), producing conservative but potentially misleading inference. For IPBL, the state-year cluster is *coarser than the treatment cell* along some dimensions (protection-type, family-status, month-within-year) but *finer than the policy variation* along others (reforms are state-level, not state-year). The authors commendably report wild-cluster bootstrap CIs and six alternative cluster levels. But the paper does not articulate *why* state x year-of-protection is the headline choice rather than, say, district x year (for IVUR) or state (for IPBL).

**Why this matters.** For a credibility-focused AER submission, the standard-error strategy must be justified explicitly. A referee should be able to answer "at what level is the treatment assigned?" and then verify that clustering matches. Here, neither treatment matches the headline cluster.

**Suggestion.** The paper should add a paragraph in Section 4.1 explaining the logic of the clustering choice -- specifically, why state x year-of-protection is chosen as a conservative compromise. The authors should explicitly discuss the two-treatment, two-scale problem and explain which alternative clustering results they consider most informative for each treatment. The robustness figure (currently in the appendix) could be promoted to the main text or at minimum referenced more prominently. Absent the ability to run new analysis, the paper should at minimum acknowledge in the main text that the headline IPBL-employment confidence intervals widen to include zero under the wild-cluster bootstrap.

**What would change my mind:** A paragraph in the methods section that (a) states which clustering level the authors consider correct for each treatment and why, (b) explicitly notes the tension between the two scales, and (c) references the bootstrap evidence as a resolution.

---

### MC2: IPBL identification rests on a small number of state-level reforms, and the confounding concern is acknowledged but not bounded

**Dimension:** #1 (Identification)
**Severity:** MAJOR

**Description.** The IPBL variation comes primarily from four reforms in three states (Lower Austria April 2016, Upper Austria July 2016, Lower Austria January 2017, Burgenland April 2017). With district FE and month-year FE, the identifying variation for IPBL is within-state, within-time deviation from the district mean -- but because IPBL varies at the state level (not the district level), the district FE do not absorb state-level trends. The authors acknowledge (4_method.tex, line 81) that "The welfare reforms... might result from a broader change in attitudes towards refugees." They provide a useful signing argument: the IPBL coefficient on employment is a *lower bound* (in absolute terms) and the IPBL coefficient on mobility is an *upper bound*. This is honest and valuable. However, the paper does not go further.

**Why this matters.** The paper's headline finding includes the IPBL effect and the IVUR x IPBL interaction. If the IPBL coefficient is confounded by anti-refugee sentiment, then the interaction result is also contaminated.

**Suggestion.** The paper should discuss more explicitly the effective number of policy experiments generating IPBL variation. The bounding argument in Section 4.2 is good but should be expanded: can the authors state what magnitude of attitude-driven confound would be needed to fully explain the IPBL employment effect? This back-of-the-envelope calculation does not require new regressions -- it is a framing exercise using the already-reported FPÖ vote-share results.

**What would change my mind:** (a) An explicit statement of how many policy events drive the IPBL variation; (b) a back-of-the-envelope bounding exercise using the FPÖ vote-share results; (c) differentiated language about the credibility of the two treatments throughout the paper.

---

### MC3: Pre-trends analysis is missing from the compiled manuscript

**Dimension:** #1 (Identification)
**Severity:** MAJOR

**Description.** For a paper that estimates the effect of initial conditions at the moment of labor market entry on monthly outcomes from month 0 through month 60, showing that there is no relationship between the treatments and outcomes *before* treatment is a fundamental diagnostic. The balance table tests whether individual characteristics predict IVUR/IPBL, which is necessary but not sufficient. What matters for identification is whether *outcomes* before treatment are flat in IVUR and IPBL. Given that employment is near-zero before protection, the pre-trends test has limited power for employment. But for mobility, welfare receipt, and PES usage, pre-trends are informative and should be shown.

**Why this matters.** An AER referee will ask: "If I see the effect materialize at month 0, can I be sure nothing was already happening at month -6?"

**Suggestion.** The pre-trends figures appear to already exist. The paper should include them in either the main text or a prominently referenced appendix, with explicit discussion of what they show.

**What would change my mind:** Inclusion of the pre-trends analysis in the manuscript with explicit discussion.

---

### MC4: IVUR is constructed over a 3-month forward window, creating a mechanical overlap with early outcomes

**Dimension:** #2 (Estimation) / #1 (Identification)
**Severity:** MAJOR

**Description.** The IVUR is defined as the sum of open positions divided by the sum of unemployed individuals over months t=0 to t=2 after protection (Equation 1). This means the treatment variable includes labor market conditions in the *same months* as the earliest outcomes. Whatever local shock raised the IVUR in months 0-2 is the same shock that raised employment in months 0-2. The district FE absorb the permanent level, but a transient positive shock to district d in month t=0 raises both IVUR and employment mechanically.

**Why this matters.** The IVUR coefficient at months 0-2 may partly capture a contemporaneous correlation rather than a causal effect. This concern fades for outcomes beyond month 2.

**Suggestion.** The paper should discuss the 3-month averaging window explicitly and acknowledge that months 0-2 estimates may be mechanically contaminated. A sentence such as "Because the IVUR window overlaps with the first three outcome months, the estimates at t=0-2 should be interpreted cautiously; the effect at t=3 and beyond is free of this mechanical overlap" would suffice.

**What would change my mind:** A brief discussion of the 3-month window choice, explicit acknowledgment of the mechanical overlap, and guidance that the month-3+ estimates are the clean estimates.

---

## Minor Concerns

### mc1: Conditional wage analysis has an unbounded selection problem

The paper estimates log wages conditional on employment and acknowledges the selection concern in a footnote. Since IVUR raises employment probability, the employed population under high IVUR includes marginal workers who would not be employed under low IVUR. If marginal workers earn less, the conditional wage estimate is downward-biased. The paper should note the direction of this bias explicitly.

### mc2: Multiple testing across ~600 outcome-month regressions

The paper estimates separate regressions for each of approximately 60 outcome months and for approximately 10 outcome variables. No multiple-testing adjustment is applied. A sentence acknowledging this and noting that readers should focus on the pattern of effects over time rather than on the significance of any individual month-coefficient would be appropriate.

### mc3: The "standard shift" reporting convention needs explicit cross-reference

The standard shift of 0.2 for IVUR is 31% larger than one SD (0.153). The paper should be more explicit that 0.2 is closer to the IQR than the SD.

### mc4: Policy simulation assumes linearity

The counterfactual simulations in Section 7 use linear OLS coefficients to predict outcomes under alternative IPBL levels. The paper should note that these simulations assume linearity and that the estimated effects may not extrapolate to large changes.

### mc5: Leave-one-state-out analysis uses a modified specification

The leave-one-state-out robustness adds family-benefits x state x protection-type interactions when dropping states. This changes the identifying variation. The paper should note this more prominently.

### mc6: Number of clusters not reported

The paper should state the exact number of clusters. Cameron and Miller (2015) recommend this as standard practice.

---

## Positive Observations

1. **Transparent identification discussion.** The two-level argument (Section 4.2) is clearly structured. The separate treatment of IVUR and IPBL identification, including the honest acknowledgment that IPBL is weaker, is commendable.

2. **Balance table is well-constructed.** Table 1 reports both specifications (with and without arrival-group FE), includes a joint Wald test, and shows coefficient magnitudes alongside significance.

3. **Wild-cluster bootstrap with Webb weights.** Best-practice for few-cluster inference. The paper's acknowledgment of Austria's small number of states is honest and valuable.

4. **Honest treatment of IPBL weakness.** The bounding argument (Section 4.2) -- signing the direction of bias separately for employment and mobility -- is a textbook example of how to handle an imperfect instrument.

5. **Mechanisms analysis is targeted rather than theatrical.** The occupation-specific IVUR decomposition directly tests the "immediate constraints vs. forward-looking" interpretation.

---

## Methods-Referee Sanity Checks (Summary)

| Check | Status | Notes |
|---|---|---|
| Identifying assumption stated cleanly? | Yes | Section 4.2: two conditional independence assumptions stated formally. |
| Treatment definition matches data construction? | Yes, with caveat | IVUR's 3-month forward window creates overlap (MC4). |
| Sample inclusion/exclusion documented end-to-end? | Yes | Section 3.1 documents all restrictions; appendix tests for selection. |
| Standard errors match design? | **No** | See MC1. Clustering at state x year does not match either treatment's variation level. |
| Functional form choices justified? | Mostly | OLS with linear treatment effects is standard but nonlinearity not discussed. |
| Multiple-testing concerns surfaced? | No | See mc2. 600+ regressions with no MHT discussion. |
| Effect sizes economically meaningful? | Yes | 4 pp employment effect off 11.3% base is large (35%). |
| Robustness checks address obvious threats? | Mostly | Missing: pre-trends (MC3), explicit discussion of IVUR window overlap (MC4). |

---

**Overall assessment.** The IVUR identification strategy is well-executed and would satisfy a skeptical non-specialist. The IPBL identification is acknowledged as weaker but needs more explicit bounding. The clustering choice requires a principled justification. The missing pre-trends and the IVUR forward-window overlap are resolvable concerns. With these revisions -- all prose/framing, not new analysis -- the paper would be substantially stronger.
