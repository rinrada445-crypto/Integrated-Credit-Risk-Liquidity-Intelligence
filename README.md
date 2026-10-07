# Integrated Credit Risk & Liquidity Intelligence

**Monitoring Portfolio Health for Cash Flow Stability**

<img width="1098" height="707" alt="Screenshot 2026-10-07 200021" src="https://github.com/user-attachments/assets/26fa5e50-b5a2-4db0-bd3d-a8386615a35b" />


## Overview

In the credit card industry, balancing **credit risk** and **financial liquidity** is essential for sustainable growth. This project analyzes customer payment behavior and evaluates default risk that directly affects organizational cash flow.

Using a 6-month history of billing statements and actual payments, the interactive dashboard gives risk managers and executives **early warning signals**. It combines industry-standard metrics — **NPL Ratio**, **Average Credit Utilization Rate**, and **Cash Gap** — with demographic segments (age, gender, education, marital status).

The insights support more accurate risk-based customer segmentation, which in turn enables data-driven credit limit allocation, proactive collection strategies, and long-term liquidity stabilization.

## Key Metrics

| Metric | Value |
|---|---|
| Total accounts | 30,000 |
| Total bill amount (6 months) | 8.10 bn |
| Total payment amount | 949.54 M |
| Collection rate | 11.73% |
| Cash Gap (uncollected) | 7.15 bn (88.27% of billed) |

Only about 11.7% of billed amounts were collected over the period. The remaining **7.15 billion** forms a cash flow gap, signalling severe liquidity risk driven by widespread payment shortfalls.

## Dataset

Source: [Default of Credit Card Clients — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients)

The binary response variable is **Default Payment**. The dataset has 23 standard explanatory variables, plus custom risk metrics built for this project.

### Original variables

| Variable | Description |
|---|---|
| `LIMIT_BAL` | Amount of given credit (individual + family/supplementary credit) |
| `SEX` | 1 = male, 2 = female |
| `EDUCATION` | 1 = graduate school, 2 = university, 3 = high school, 4 = others |
| `MARRIAGE` | 1 = married, 2 = single, 3 = others |
| `AGE` | Age in years |
| `PAY_1` – `PAY_6` | Repayment status, September back to April 2005 (-1 = paid duly, 1–9 = months of delay; 9 = nine months or more) |
| `BILL_AMT1` – `BILL_AMT6` | Bill statement amount, September back to April 2005 |
| `PAY_AMT1` – `PAY_AMT6` | Previous payment amount, September back to April 2005 |

### Engineered metrics

- **Cash Gap** — Bill Amount − Pay Amount. A direct proxy for outstanding liquidity strain.
- **NPL Ratio** — Outstanding balances of cardholders in critical delinquency (30 or 90+ days past due) relative to the portfolio's total credit exposure.
- **Average Credit Utilization Rate** — Aggregate billed amounts over the 6-month window relative to the total approved credit limit. Used as an early warning indicator.

## Analysis & Findings

### 1. Repayment behavior by age cohort

| Age group | Observation |
|---|---|
| **31–40** | Largest contributor to repayments (peaking above 70M/month), but also carries the highest billing and credit exposure |
| **21–30** | Stable and predictable payments of roughly 45M–55M/month, consistent with fixed-income or minimum-payment habits |
| **41–50** | Moderate contraction, averaging 30M–40M/month |
| **51–60** | Marginal contribution, below 10M/month |
| **61+** | Negligible, around 0–1M/month |

### 2. Cash Gap by gender

![Cash Gap by Gender](assets/cash-gap-gender.png)

Female cardholders account for a Cash Gap of **over 4.18 bn**, versus about **2.97 bn** for males. Liquidity strain is concentrated in the female segment, which also shows the highest delinquency and payment delay rates.

### 3. Cash Gap by education level

![Cash Gap by Education](assets/cash-gap-education.png)

| Education | Cash Gap |
|---|---|
| University | 3.54 bn |
| Graduate school | 2.38 bn |
| High school | 1.08 bn |
| Others / unknown | ~0.14 bn |

University and graduate-school holders together account for **5.92 bn** of the deficit (over 80% of the total). Credit limits for highly educated applicants should be re-evaluated.

### 4. Cash Gap by marital status

![Cash Gap by Marital Status](assets/cash-gap-marital.png)

| Marital status | Cash Gap |
|---|---|
| Single | 3.70 bn |
| Married | 3.38 bn |
| Others | 0.06 bn |
| Unknown (0) | 0.01 bn |

## Key Insights

1. **The education–underwriting paradox.** Risk is not concentrated in lower-education segments. Degree holders, who largely overlap with the 31–40 core working population, hold the bulk of the deficit. This suggests credit limits (`LIMIT_BAL`) were allocated on profile prestige rather than cash flow reliability and repayment discipline.
2. **Systemic financial strain.** Single and married cardholders have similar gaps, and the NPL Ratio is roughly **20% across all age groups**. This points to a portfolio-wide problem rather than one isolated behavioral segment.
3. **Risk epicenter.** The highest delinquency, longest payment delays, and most disproportionate Cash Gap sit with **single female cardholders aged 21–40**, the priority target for risk containment.

## Recommendations

**Short term**
- Deploy an early warning system based on the **Credit Utilization Rate** for the 21–40 age bracket.
- Freeze limits on accounts with near-maximum utilization and declining payment amounts (`PAY_AMT`).

**Long term**
- Recalibrate the credit scoring model: reduce the predictive weight of `EDUCATION` and penalize historical payment delays (`PAY_1`–`PAY_6`) more heavily.
- Move from a one-size-fits-all policy to a targeted risk control framework with segment-specific collection strategies.

## Repository Structure

```
.
├── README.md
├── assets/          # dashboard screenshots and charts
├── data/            # dataset (see Dataset section)
└── ...
```

## Getting Started

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
```

<!-- Add install and run instructions for your dashboard here -->

## License

Add your license here (e.g. MIT). The dataset is subject to the terms of the UCI Machine Learning Repository.
