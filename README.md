# MasterControl Sales Analytics — Mx Lead Targeting

**Author:** Rob Sheehy | MSBA Capstone Group 5
**Tools:** R, tidyverse, ggplot2, logistic regression, random forest

---

## The Business Problem

MasterControl sells two software products to life sciences companies — Qx for quality management and Mx for manufacturing execution. Qx converts sales leads at 19.7% but Mx is only hitting 12.7%. The goal was to figure out which companies and which people within those companies actually convert for Mx, and build something the sales team can act on.

We analyzed 16,644 Qualified Account Lead records from 2024–2025. A lead progressed if it moved to SQL, SQO, or Won.

---

## My Individual EDA (`MasterControl_EDA_Rob.Rmd`)

My focus was an Mx deep dive — finding where Mx actually works and why it underperforms everywhere else.

Key things I found:

- Small companies convert best for Mx at 15.6% while Large companies are only at 5.5% — the opposite of what I expected
- Medical Device + Small + Mx converts at 20.3% and Pharma + Small + Mx at 19.0% — both well above the 12.7% baseline
- Quality titles dominate the dataset (3,096 occurrences vs 477 manufacturing titles) — MasterControl is reaching Quality personas who care about QMS, not Manufacturing personas who need MES. That's a core part of why Mx underperforms
- 40.9% of manufacturing model and site function data was missing — flagged throughout as a key limitation

---

## My Individual Modeling (`MasterControl_Modeling_Rob.Rmd`)

Built my own modeling notebook focused on predicting which Mx leads are most likely to convert and translating that into a practical sales targeting framework.

**What I built:**

- Rule-based title classification system converting 6,400+ unique job titles into seniority and functional role categories, plus binary keyword flags for overlapping title signals
- Logistic Regression as the primary model — selected for interpretability so the sales team can understand why each lead is prioritized
- Random Forest as a benchmark to validate the same variables dominate across approaches
- AUC of 0.663 — solid for sales conversion data with significant class imbalance and missing values

**Mx Lead Prioritization Framework — core deliverable:**

Used the logistic model to score every Mx lead with a predicted conversion probability, then bucketed them into three tiers:

| Tier | Leads | Conversion Rate | vs Baseline |
|------|-------|----------------|-------------|
| Tier 1 (score ≥ 0.25) | 295 | 33.2% | +19.8pp |
| Tier 2 (score 0.15–0.25) | 762 | 16.9% | +3.5pp |
| Tier 3 (score < 0.15) | 2,092 | 9.4% | -4.1pp |

Tier 1 profile: Small Pharma & BioTech, in-house manufacturing, Manager level contacts. 66% of current Mx SDR effort is going to Tier 3 leads converting below baseline. Redirecting effort toward Tier 1 produces a 2.5x improvement without generating any new leads.

---

## Business Recommendations

- SDRs should focus on small manufacturers — CMO, CDMO, and in-house accounts — and pull back on services and software
- Marketing should shift spend toward contract manufacturing channels
- Sales leadership should implement tier scoring in CRM so reps work from a ranked list instead of treating all Mx leads equally
- Run a one-quarter pilot on Tier 1, validate the lift holds, then scale

---

## Files

| File | Description |
|------|-------------|
| `MasterControl_EDA_Rob.Rmd` | Individual EDA notebook |
| `MasterControl_EDA_Rob.html` | Rendered EDA output |
| `MasterControl_Modeling_Rob.Rmd` | Individual modeling notebook |
| `MasterControl_Modeling_Rob.html` | Rendered modeling output |

*Note: Project data not included per course policy.*
