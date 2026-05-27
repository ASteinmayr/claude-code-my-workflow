# Future Revision Inspections — Opportunities or Benefits

**Created:** 2026-05-19
**Source:** items deferred during the ReStud-bound revision pass (Batch B of `/proofread` follow-up).

These items were identified during the proofreading and editorial review (see [article_proofread_report.md](article_proofread_report.md) and [peer_review_opportunities_or_benefits/editorial_decision.md](peer_review_opportunities_or_benefits/editorial_decision.md)) but deferred — either because they need analysis the current revision can't do, or because they're better handled alongside other tasks. Address before the next submission round.

---

## C3 — Reconcile §3 statement with Appendix finding on PES-registration / IVUR correlation

**Location:** [3_data.tex:8](../articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/3_data.tex#L8) ↔ [appendix.tex:238](../articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/appendix.tex#L238)

**The contradiction.**

`3_data.tex:8` currently says:
> "we test whether the number of refugees in our data, as a share of all individuals from those countries of origin in a district, correlates with our main explanatory variables, **which is not the case**."

`appendix.tex:238` says:
> "In columns (4)-(5), where we use the overall shares as an outcome, **the effect of the IVUR becomes statistically significant at the 5% level** ... This positive relation hints at a positive effect of IVUR on registration with the PES. If the individuals who register when the labor market is tight but not otherwise are individuals who are relatively more inclined to take up employment, our estimates for the effect of IVUR on employment might be upward biased. However, the magnitude of such a bias is minor."

The §3 statement directly contradicts what the appendix actually shows.

**Why deferred.** Three reasonable resolutions, but each commits to a substantive claim about the direction and magnitude of bias. Cleanest to address alongside the bigger revision items where the implications can be coordinated.

**Options (from the proofread report):**

- (a) Soft acknowledgment: "While the magnitude is small, we find a statistically significant positive correlation with the IVUR in the aggregated specification (see Appendix \ref{subsec:pes_selection})."
- (b) Minimal qualification: "The correlation is generally small, though statistically significant for the IVUR in some specifications (see Appendix \ref{subsec:pes_selection})."
- (c) Direction-of-bias hedge: "...suggesting our IVUR estimates may be modestly upward biased. The magnitude is too small to materially affect our main conclusions."

**Recommended approach when addressed.** Pair with the response-to-referees stage. A CREDIBILITY referee will catch this contradiction on first read — fixing it strengthens the manuscript regardless of which direction-of-bias hedge is chosen.

---

## C5 — Move IPBL rescaling into the R script that produces Table 1

**Location:** [tables/descriptives_manually_edited.tex](../articles/Opportunities_or_Benefits__Local_Conditions_and_Refugee_Labor_Market_Integration/tables/descriptives_manually_edited.tex) (currently edited manually)

**Background.** Table 1's IPBL row was rescaled from raw euros (€826.87 / €518.66 / €763.99) to €1,000 units (0.83 / 0.52 / 0.76) on 2026-05-19 to match the convention used throughout the regression analysis and all figures. The change was made by hand-editing the `.tex` file, but the file is described in its filename as "manually_edited" — implying that earlier values likely come from an R script (or were originally generated, then partially hand-tuned).

**Risk.** If the R script that originally produced this table is re-run, the IPBL values will be regenerated in raw euros and overwrite the hand-edit. The unit convention will silently break again.

**Action.** Locate the R script that generates Table 1's underlying data. Update it so that IPBL is divided by 1,000 at the table-output stage. Re-export. Confirm Table 1 still renders 0.83 / 0.52 / 0.76 after the script-regenerated values land in `descriptives_manually_edited.tex`.

**Recommended approach when addressed.** Do this as part of the broader replication-script audit, since IPBL rescaling propagates anywhere else IPBL is displayed (currently only Table 1 in the main text — but check `tables/*.tex` for any other IPBL displays).

---

## Lesson — be careful with "submission-ready" bib pruning

**On 2026-05-22**, the `degenhardt2025` entry was found to have been over-pruned during an earlier Option D bibliography cleanup pass. At the time, it was uncited and was therefore swept up in the "drop all unused" pass. Three sessions later it turned out to be one of two concurrent Austrian-dispersal papers the manuscript needed to differentiate from, so the entry had to be restored.

**Rule of thumb for future pruning passes:** preserve uncited entries by an author who is already cited elsewhere (especially same-year working papers), since the manuscript may need to cite the variant as concurrent or related work later. The cost of keeping a few uncited entries is much smaller than the cost of restoring a dropped entry and re-verifying its bibliographic details mid-revision.

---

## How to use this file

- Add new items whenever a revision decision is made to defer rather than apply.
- When a deferred item is finally addressed, leave the entry but note the resolution + date.
- Cross-link to the response-to-referees document when one is drafted, so the editor can see how each editorial finding was either addressed in revision or explicitly deferred.
