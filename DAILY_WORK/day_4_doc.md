# Notebook 06: Survival Analysis

## Overview

Notebook 06 applies survival analysis techniques to the Telco Customer Churn dataset as part of **CHURNIQ — Customer Lifetime Value and Churn Intelligence System**.

The notebook explores customer tenure, estimates survival probabilities, compares survival patterns across contract types, and uses a Cox proportional hazards model to investigate factors associated with customer churn.

## Objectives

- Estimate customer survival probabilities using the Kaplan–Meier estimator.
- Compare survival patterns across different contract types.
- Perform a log-rank test to compare selected contract groups.
- Build a Cox proportional hazards model to analyze factors associated with churn.
- Generate visualizations and export results for further analysis.

## Techniques Used

### 1. Kaplan–Meier Survival Analysis

The Kaplan–Meier estimator is used to estimate the probability that customers remain active over the observed tenure period.

### 2. Survival Analysis by Contract

Survival curves are compared across contract types to explore differences in customer retention patterns.

### 3. Log-Rank Test

The log-rank test is used to assess whether the survival curves of the selected contract groups differ statistically.

### 4. Cox Proportional Hazards Model

The Cox model examines associations between customer characteristics and churn risk. Depending on the available dataset columns, the model may include:

- Contract type
- Monthly charges
- Senior-citizen status
- Internet service
- Paperless billing
- Payment method

Categorical variables are converted into numerical indicator variables before model fitting.

## Input Dataset

The notebook uses the Telco Customer Churn dataset.

Expected file path:

`C:\CHURNIQ\SQL\psql telco_customers_data.csv`

Update the path if the dataset is stored in a different location.

## Libraries Used

- `pandas`
- `numpy`
- `matplotlib`
- `lifelines`

Install the required survival-analysis library if necessary:

```python
%pip install lifelines
```

## Expected Outputs

All outputs are saved in the `../reports/survival/` directory relative to the notebook's working directory.

| File Name | Description |
|---|---|
| `kaplan_meier_overall.png` | Overall Kaplan–Meier survival curve |
| `kaplan_meier_by_contract.png` | Survival curves grouped by contract type |
| `kaplan_meier_survival_curve.csv` | Survival probabilities across tenure values |
| `contract_logrank_test.csv` | Log-rank test statistic and p-value |
| `cox_hazard_ratios.csv` | Cox model coefficients, hazard ratios, confidence intervals, and statistical results |
| `cox_coefficients.png` | Visualization of Cox model coefficients |
| `survival_analysis_summary.csv` | Summary statistics and selected model results |

These are the expected output files. They will be available after the corresponding notebook cells execute successfully.

## How to Run

1. Open Notebook 06 in Jupyter Notebook.
2. Verify the input dataset path.
3. Install `lifelines` if it is not already installed.
4. Run the notebook cells sequentially.
5. Review the Kaplan–Meier curves, contract comparisons, log-rank test, and Cox model results.
6. Verify that the expected files have been generated in `reports/survival/`.

## Limitations

The standard Telco Customer Churn dataset is a snapshot and does not provide complete longitudinal records of each customer's exact churn time. Therefore, using tenure and churn status for survival analysis is an exploratory approximation.

- Survival estimates should not be treated as validated predictions of exact customer lifetime.
- Cox model hazard ratios describe associations and do not establish causation.
- The proportional hazards assumption should be checked before interpreting the Cox model.
- More reliable lifetime estimates require appropriately defined observation periods and accurate event or censoring times.

## Project Contribution

Notebook 06 adds a survival-analysis perspective to the CHURNIQ churn prediction workflow. Its outputs can support further customer retention and customer lifetime value analysis, provided the limitations of the available dataset are considered.
