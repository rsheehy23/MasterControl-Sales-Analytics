# MasterControl-Sales-Analytics
Sales lead analysis and predictive modeling for MasterControl's Mx product line
# MasterControl Sales Analytics — Mx Lead Targeting

**Author:** Rob Sheehy | MSBA Capstone Group 5
**Tools:** R, tidyverse, ggplot2, logistic regression, random forest, XGBoost

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
- 40.9% of manufacturing model and site function data was missing — flagged this throughout as a key limitation

---

## Group Modeling (`Modeling_Mastercontrol_Group_5_Final.Rmd`)

Group modeling notebook combining work from all team members. My contributions include the Mx Lead Prioritization Framework (tier scoring system) and portions of the executive analysis and deliverable sections.

The team built five models — Logistic Regression, Elastic-Net, Decision Tree, Random Forest, and XGBoost. My contribution was the Mx Lead Prioritization Framework which used the combined logistic regression model to score every Mx lead with a predicted conversion probability and bucket them into three tiers:

| Tier | Leads | Conversion Rate | vs Baseline |
|------|-------|----------------|-------------|
| Tier 1 (score ≥ 0.25) | 310 | 32.9% | +19.4pp |
| Tier 2 (score 0.15–0.25) | 783 | 17.0% | +3.5pp |
| Tier 3 (score < 0.15) | 2,051 | 9.2% | -4.3pp |

Tier 1 profile: Small Pharma & BioTech, in-house manufacturing, Manager level contacts. 65% of current Mx SDR effort is going to Tier 3 leads converting below baseline. Redirecting effort toward Tier 1 produces a nearly 2.5x improvement without generating any new leads.

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
| `MasterControl_EDA_Rob.Rmd` | My individual EDA notebook |
| `MasterControl_EDA_Rob.html` | Rendered EDA output |
| `Modeling_Mastercontrol_Group_5_Final.Rmd` | Group modeling notebook |
| `Modeling_Mastercontrol_Group_5_Final.html` | Rendered modeling output |

*Note: Project data not included per course policy.*
