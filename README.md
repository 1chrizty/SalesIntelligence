# SkyGeni — Sales Intelligence Challenge

**Role:** Data Science / Applied AI Engineer  
**Objective:** Design a decision intelligence system that helps a CRO understand why win rate is dropping despite healthy pipeline volume, and what actions to take.

---

## Approach

The focus of this project is not to build a highly accurate ML model.  
The focus is to convert historical sales data into operational insights that a CRO can act upon.

The project is structured into:

1. **Problem Framing** — Understanding the real business issue behind falling win rates.
2. **Exploratory Data Analysis** — Identifying where pipeline leakage occurs.
3. **Custom Metric Design** — Creating metrics that expose hidden issues:
   - Qualification Leakage Rate (QLR)
   - Rep Impact Index (RII)
4. **Decision Engine** — Using an interpretable model to identify drivers of win/loss.
5. **Sales Insight System Design** — Designing how this would work as a real product.
6. **Reflection** — Understanding limitations and real-world challenges.

The analysis and insights were done in Python (Colab) for CRO-level understanding.

---

## Key Business Insights Identified

- Major deal leakage occurs at the Qualified stage → poor qualification.
- Large rep performance variance → people/process issue.
- Partner lead source produces lower win rates → pipeline quality issue.
- Deal size and sales cycle length are similar for won and lost deals → pricing and speed are not the problem.

---

## Custom Metrics Designed

### Qualification Leakage Rate (QLR)
Percentage of deals entering the Qualified stage that end as lost.

### Rep Impact Index (RII)
(Rep win rate − Org win rate) × Number of deals handled.

These metrics highlight hidden operational issues rather than surface-level win rate.

---

## Decision Engine (Win Rate Driver Analysis)

Instead of predicting deal outcomes, Logistic Regression was used to extract feature impacts.

Features used:
- deal_stage
- sales_rep_id
- industry
- region
- product_type
- lead_source

The model is used to answer:

> Which factors are hurting or improving win rate?

This allows leadership to take action on:
- Qualification process
- Rep coaching
- Lead source evaluation
- Stage process improvement

---

## Sales Insight & Alert System Workflow

CRM → ETL → Feature Metrics (QLR, RII, Stage Win Rate) → Driver Model → Insight Engine → Dashboard / Alerts

Example alerts:

- Qualified stage win rate dropped this week
- Partner leads causing higher losses
- Rep underperforming vs team average
- Region + product combination showing unusual loss pattern

Runs daily with weekly summary for CRO.

---

## Reflection

### Weak Assumptions
- Deal stage treated as meaningful progression without stage history
- Accurate CRM tagging assumed

### Real-World Challenges
- Poor CRM discipline
- Missing data
- Seasonal and strategy changes

### If given 1 month
- Add stage transition timeline
- Add email/call activity data
- Add text analysis of call notes
- Build pipeline forecasting

---

## How to Run the Project (Google Colab)

1. Open the notebook: `notebook/sales_intelligence_analysis.ipynb`
2. Upload `skygeni_sales_data.csv` to Colab
3. Run all cells in order
4. Observe insights and model outputs

---

## Key Decisions Made

| Decision | Reason |
|----------|--------|
| Use Logistic Regression | Interpretability over complexity |
| Design custom metrics (QLR, RII) | Reveal hidden operational issues |
| Focus on drivers, not prediction | Align with business problem |
| Emphasize system design | Reflect real Applied AI role |

---

## Final Note

This project focuses on transforming sales data into decision intelligence by identifying operational drivers of win rate and presenting them in a way that leadership can act upon.
