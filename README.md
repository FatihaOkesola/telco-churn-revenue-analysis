# Customer Churn and Revenue Retention Analysis

Operational analysis of customer churn for a California telecom provider, framed from the perspective of a revenue analyst: why customers leave, how much recurring revenue leaves with them, and which of the drivers the company can influence.

**Status:** In progress. Parts 1 to 4 (audit, cleaning, derived variables, baseline) are complete. Analysis questions are being added.

## Data

IBM's public Telco Customer Churn sample (7,043 customers, 33 columns, one row per customer). The data is synthetic, so the results demonstrate method and are not findings about a real company. 

## Notebook structure

| Part | Contents |
|---|---|
| 1. Data audit | Grain, missing and disguised-missing values, data types, range and consistency checks, uninformative columns, extreme values |
| 2. Cleaning | Column names, Total Charges conversion with a flag column, zip codes as text, dropped and set-aside columns, cleaning log, validation checks |
| 3. Derived variables | Tenure bands, service and add-on variables, automatic payment, household, annual revenue estimate, churn reason groups with a validated merge |
| 4. Baseline | Customer churn rate, revenue churn rate, annual revenue estimate |
| 5. Analysis | Churn reasons by customers and revenue (more questions in progress) |

## Key points on the data

- Total Charges loads as text because of 11 blank strings, all customers with a tenure of 0 months. They are flagged and left missing, not filled.
- `churn_score` and `cltv` are IBM model outputs, so they are set aside and not used to explain churn.
- "No phone service" and "No internet service" are kept as genuine labels, because they show which customers could not buy a service.
- Revenue figures use monthly charges multiplied by 12. They are estimates, since the data has no billing history.

## Run it

Python 3.10 or later.

    pip install -r requirements.txt
    jupyter notebook Telco_churn.ipynb

## Tools

Python, pandas, NumPy, matplotlib, SciPy, statsmodels.
