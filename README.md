# Customer Churn Analysis — End-to-End Data Analytics Project

## Overview
An end-to-end customer churn analysis for a subscription-based OTT business using SQLite, SQL, Python, pandas, NumPy, Matplotlib and Seaborn.

The project answers four business questions: **Who is churning? Why? When? Which customers should be prioritized for retention?**

> **Dataset note:** The supplied database contains 21 customers. Results are portfolio/demo findings and should be validated on a larger production dataset.

## Business Objectives
- Measure churn and retention.
- Compare churn by plan and contract.
- Identify geographic and monthly churn patterns.
- Quantify monthly revenue exposed to churn.
- Segment customers using the existing `churn_score`.
- Examine support escalation as a churn-related signal.
- Convert analysis into actionable retention recommendations.

## Data Architecture
| Table | Purpose |
|---|---|
| `db_customer` | Customer demographics and geography |
| `db_subscription` | Subscription, plan, contract, charges, CLTV, churn score |
| `db_support` | Complaints, escalations and CSAT |

All tables are connected using `customerid`.

## Tech Stack
Python · Pandas · NumPy · SQLite · SQL · Matplotlib · Seaborn · Jupyter Notebook

## Analytical Workflow
1. Extract relational data from SQLite using SQL and Python.
2. Clean names, dates, categories and missing country values.
3. Create `churn_flag` from `cancellation_date`.
4. Calculate complaint counts and customer tenure.
5. Merge customer, subscription and support data.
6. Calculate KPIs and segment customers by risk.
7. Visualize churn patterns.
8. Translate findings into retention actions.

## KPI Snapshot
| KPI | Result |
|---|---:|
| Customers | 21 |
| Churn rate | 28.6% |
| Retention rate | 71.4% |
| ARPU | ₹18.85 |
| Average tenure | 1,560 days* |
| Total monthly charges | ₹395.79K* |
| Revenue at risk | ₹73.94K* |
| Revenue exposed | 18.7% |
| Escalation rate | 19.0% |
| Escalation–churn correlation | 0.47 |

## Key Findings

### 1. Contract Type
Monthly-contract customers churn at **55.6%**, versus **8.3%** for annual customers.

### 2. Plan Type
Basic has the highest observed churn at **60.0%**, followed by Standard and Premium.

### 3. Geography
Karnataka shows **100% churn (2/2 customers)** in this sample. This is an investigation signal, not a population-level conclusion.

### 4. Timing
September 2024 has the highest monthly churn concentration, with two cancellations.

### 5. Revenue
Churned customers account for approximately **₹73.94K in monthly charges**, around **18.7%** of total monthly charges.

### 6. Risk Segmentation
Customers with `churn_score >= 70` are classified as High Risk. Six customers fall into this segment and all six are churned in the supplied dataset.

### 7. Cancellation Drivers
Observed reasons include competitor switching, price sensitivity, insufficient content, poor streaming quality and trial cancellation.

### 8. Support
Escalation vs churn correlation is approximately **0.47**. This indicates association in the small sample, not causation.

## Recommendations
- Run monthly-to-annual migration experiments.
- Investigate Basic-plan pricing, content and service quality.
- Investigate the Karnataka outlier.
- Prioritize high-risk customers using churn score + CLTV + monthly charges + support history.
- Create targeted retention playbooks by cancellation reason.
- Use support escalation as an early-warning signal and validate it with more data.

## Limitations
- Only 21 customers are present.
- Analysis is descriptive/diagnostic, not causal.
- `churn_score` is an existing dataset field; this notebook does not train a model to generate it.
- Support records are consolidated to the latest record after complaint counts are calculated.
- Geographic percentages require validation on a larger dataset.
