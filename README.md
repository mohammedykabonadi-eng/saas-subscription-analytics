# SaaS Subscription Churn & Revenue Analytics

End-to-end data analytics project covering **Excel → SQL → Power BI**, analyzing churn, revenue, and customer health for a simulated B2B SaaS company (2022-2025).

## Business Problem

A SaaS company with 3,000 customers has a 36.3% subscription churn rate. This project identifies **which segments churn most, why they leave, how much revenue is at risk, and which customers to prioritize for retention outreach** — using a realistic, relational dataset built to mirror a real subscription business (plans, billing cycles, usage, support tickets, and payment failures).

## Dataset

Synthetic but realistic data generated with Python (not sourced from Kaggle), covering:

| Table | Rows | Description |
|---|---|---|
| `customers` | 3,000 | Company profile, industry, acquisition channel, signup date |
| `subscriptions` | 3,000 | Plan, billing cycle, seats, MRR, status, cancel reason |
| `payments` | 32,916 | Payment history, status (paid/failed/refunded), method |
| `usage_monthly` | 56,422 | Monthly active users, logins, API calls, feature usage |
| `support_tickets` | 13,337 | Category, priority, resolution time, satisfaction score |
| `plans` | 4 | Free, Starter, Pro, Enterprise tiers |

Patterns are built in intentionally (e.g. churn varies by plan, channel and billing cycle; usage drops before cancellation) so the data rewards real analysis rather than being random noise.

## Tech Stack

- **Excel** — data validation, feature engineering, first-pass KPIs (all formula-driven)
- **SQL** (MySQL) — schema design, data-quality checks, business queries, star-schema views
- **Power BI** — data model, DAX measures, 4-page interactive dashboard

## Dashboard

![Overview](images/dashboard_overview.png)
![Churn Analysis](images/dashboard_churn.png)
![Revenue & Payments](images/dashboard_revenue.png)
![Customer Health](images/dashboard_customer_health.png)

### Key metrics tracked
- MRR / ARR trend and month-over-month movement
- Churn rate by plan, acquisition channel, and billing cycle
- Cancellation reasons, ranked
- Failed-payment revenue recovery opportunity
- Usage drop-off as an early churn signal
- At-risk customer list (low recent usage, still active)

## Key Insights

1. **Free and Starter plans churn 2-4x more than Enterprise** (60.3% vs. 16.2%) — upgrade paths should be a retention priority.
2. **Paid Ads customers churn more than Referral customers** (43.5% vs. 27.8%) — acquisition channel quality matters as much as volume.
3. **"Too expensive" and "Missing features" are the top two cancellation reasons**, together accounting for over 40% of all cancellations.
4. **Usage drops sharply in the final months before cancellation** — a measurable early-warning signal that could trigger proactive outreach.
5. **$6.7M in failed payments** represents directly recoverable revenue through retry logic and dunning emails.

## How to Reproduce

1. **SQL:** run `sql/01_schema.sql`, import the CSVs from `data/`, then run `02_data_checks.sql`, `03_analysis.sql`, and `04_views_for_powerbi.sql`.
2. **Excel:** open `excel/SaaS_Subscriptions_Excel.xlsx` — Summary sheet is fully formula-driven.
3. **Power BI:** open `powerbi/SaaS_Dashboard.pbix`, or load the CSVs from `powerbi/powerbi_ready/` and rebuild the model using the relationships and DAX measures documented in this repo.

## Author

**Mohammed** — Data Analyst | [GitHub](https://github.com/mohammedykabonadi-eng)
