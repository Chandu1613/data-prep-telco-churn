# Telco Customer Churn – Cleaning, EDA & Preprocessing

This project performs data cleaning, exploratory data analysis (EDA), and preprocessing on the **Telco Customer Churn dataset** to prepare it for machine learning.
---

## Dataset Summary
- **Rows:** 7,043
- **Target:** `Churn` (Yes/No)
- **Features:** Demographics, service usage, contract types, billing.
---

## Step 1: Load & Inspect

- Loaded dataset from CSV
- Found 7,043 rows and 21 columns
- Checked for nulls, data types, and sample values
---

## Step 2: Data Cleaning

- Converted `TotalCharges` to float
- Checked for duplicates
- Dropped `customerID` (non-predictive)
---

## Step 3: EDA – Target and Numeric Features

- **Churn:** 26% churn rate, slight imbalance
![churn](output/churn_distribution.png)
- **Tenure:** - Mid-range tenure (20–60 months) has fewer customers—maybe a good place to look for churn risks
![tenure](output/tenure_distribution.png)
- **MonthlyCharges:** Churners pay slightly more per month
![monthly](output/monthly_charges_boxplot.png)
---

## Step 4: Correlation & Contract Analysis

- Customers with longer `tenure` are less likely to `Churn`, indicating a negative correlation between
- Strong positive correlation between `TotalCharges` and `MonthlyCharges`, which makes sense, since TotalCharges are typically accumulated over time based on monthly billing.
![correlation](output/correlation_heatmap.png)

- Customers with Month-to-month contracts show the highest churn rate.
- over 47% of churned customers are on Month-to-month contracts, while churn among Two-year contract holders is very minimal
![contract](output/churn_by_contract.png)
---

## Outlier Detection and Removal

We visualized and removed outliers from key numeric columns using the IQR method.

- `tenure` had a clean distribution (little change)
![tenur](output/tenure_boxplot_before.png)
- `MonthlyCharges` had some high outliers removed
![monthlycharges](output/MonthlyCharges_boxplot_before.png)
- `TotalCharges` was skewed with several heavy outliers
![totalcharges](output/TotalCharges_boxplot_before.png)