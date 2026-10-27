# Notebook 09: Retention Campaign ROI Analysis

## Project Overview

**Project Name:** Customer Lifetime Value and Churn Intelligence System

**Notebook:** `09_Retention_Campaign_ROI_Analysis.ipynb`

This notebook evaluates the potential financial value of retention campaigns by combining customer churn-risk predictions from Notebook 07 with customer lifetime value (CLV) estimates from Notebook 08.

The objective is to estimate campaign costs, potential benefits, net benefits, and return on investment (ROI) under conservative, base, and optimistic retention scenarios.

> **Important:** The results are scenario-based estimates. The Telco Customer Churn dataset does not contain actual retention campaign assignments or observed campaign outcomes, so this notebook does not establish causal campaign effectiveness.

---

## Objectives

- Load customer retention-risk scores generated in Notebook 07.
- Load estimated customer lifetime values from Notebook 08.
- Identify high-risk customers for potential retention outreach.
- Define campaign cost and retention-lift assumptions.
- Estimate campaign costs and potential financial benefits.
- Compare conservative, base, and optimistic scenarios.
- Calculate estimated net benefit and ROI.
- Calculate the approximate break-even retention lift.
- Generate customer-level shortlists, CSV reports, JSON summaries, and visualizations.

---

## Technologies and Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook
- JSON and pathlib for file management

---

## Input Files

This notebook depends on the outputs from the previous project notebooks.

| Input file | Source | Purpose |
|---|---|---|
| `customer_retention_priority.csv` | Notebook 07 | Customer churn-risk predictions and prioritization |
| `customer_clv_scenarios.csv` | Notebook 08 | Estimated customer lifetime value |

Expected paths relative to the project root:

```text
reports/
├── retention/
│   └── customer_retention_priority.csv
└── clv/
    └── customer_clv_scenarios.csv
```

The customer identifier, churn-probability column, and base-scenario CLV column must be available and compatible between the two files. If the column names differ, update the column candidates in the notebook.

---

## Methodology

### 1. Load and Validate Data

Load the customer retention and CLV reports, standardize column names, merge records using customer identifiers, and validate churn probabilities and CLV values.

### 2. Select High-Risk Customers

The default threshold selects customers with a predicted churn probability of at least 60%.

This threshold is configurable and should be evaluated against the business's outreach capacity and retention objectives.

### 3. Define Campaign Assumptions

The notebook uses the following illustrative assumptions by default:

| Parameter | Default assumption |
|---|---:|
| High-risk threshold | 60% |
| Cost per contacted customer | 10 currency units |
| Conservative retention lift | 3 percentage points |
| Base retention lift | 7 percentage points |
| Optimistic retention lift | 12 percentage points |

These values are examples for scenario analysis, not measured business results. Replace them with realistic estimates when campaign-cost and outcome data become available.

### 4. Estimate Campaign Economics

For each scenario, the notebook estimates:

- Number of customers contacted
- Expected additional retained customers
- Average estimated CLV of targeted customers
- Estimated campaign benefit
- Total campaign cost
- Estimated net benefit
- Estimated ROI

The simplified calculations are:

**Campaign cost**

```text
Campaign Cost = Number of Target Customers × Cost per Contact
```

**Expected additional retained customers**

```text
Expected Additional Retained Customers
    = Number of Target Customers × Assumed Retention Lift
```

**Estimated campaign benefit**

```text
Estimated Benefit
    = Expected Additional Retained Customers × Average Target Customer CLV
```

**Estimated net benefit**

```text
Net Benefit = Estimated Benefit − Campaign Cost
```

**Estimated ROI**

```text
ROI (%) = (Net Benefit / Campaign Cost) × 100
```

These calculations assume that the CLV input represents future contribution value attributable to retaining a customer. If the CLV is based only on revenue, the calculation should be adjusted for contribution margin and relevant costs before interpreting the result financially.

### 5. Break-Even Analysis

The notebook estimates the retention lift required for the expected campaign benefit to equal the campaign cost.

This provides a useful benchmark for comparing campaign assumptions, but it does not predict the actual retention lift a campaign will achieve.

### 6. Visualization and Reporting

The notebook generates charts and machine-readable reports to support business interpretation and the final project presentation.

---

## Output Files

All outputs are saved in:

```text
reports/
└── roi/
```

| Output file | Description |
|---|---|
| `retention_roi_scenarios.csv` | Compares costs, estimated benefits, net benefits, and ROI across scenarios |
| `retention_campaign_shortlist.csv` | Lists high-risk customers selected for potential retention outreach |
| `retention_campaign_roi_scenarios.png` | Visual comparison of estimated net benefit and ROI |
| `retention_roi_break_even.json` | Stores campaign cost and break-even retention-lift calculations |
| `retention_roi_summary.json` | Stores the main assumptions, results, and analytical limitations |

These files are expected outputs after successful execution; they should not be described as generated until the notebook has been run.

---

## How to Run the Notebook

1. Complete Notebook 07 to generate the customer retention-priority report.
2. Complete Notebook 08 to generate the customer CLV scenarios.
3. Open `09_Retention_Campaign_ROI_Analysis.ipynb` in Jupyter Notebook or JupyterLab.
4. Ensure the notebook is running from the project's `notebooks/` directory.
5. Confirm that the input CSV files exist under `reports/retention/` and `reports/clv/`.
6. Execute the cells in order.
7. Review the scenario comparison, break-even calculation, and visualizations.
8. Verify that the expected files have been created under `reports/roi/`.

### Troubleshooting

- **Input file not found:** Run Notebooks 07 and 08 and verify their output paths.
- **Customer ID error:** Check that both input CSV files contain matching customer identifiers.
- **CLV column error:** Inspect Notebook 08's actual output columns and update the candidates in Cell 6.
- **No high-risk customers selected:** Review the churn-probability distribution and adjust the threshold if justified.
- **Unexpected ROI:** Verify the currency, campaign cost, retention-lift assumptions, and whether CLV represents contribution value rather than revenue.

---

## Business Value

This notebook demonstrates how churn predictions and customer-value estimates can support retention budget planning.

Potential uses include:

- Comparing hypothetical retention strategies.
- Estimating the budget required to contact high-risk customers.
- Understanding how assumed retention improvements affect potential returns.
- Identifying the minimum retention improvement needed to break even.
- Communicating model outputs in a business-oriented format.

---

## Limitations

1. **No observed campaign outcomes:** The dataset does not identify which customers received retention offers or whether those offers worked.
2. **Assumed retention lift:** Scenario values are hypothetical and must be validated using real campaign data.
3. **CLV uncertainty:** Notebook 08's assumptions directly affect the ROI estimates.
4. **Contribution value requirement:** Revenue-based CLV is not the same as profit or contribution value.
5. **Simplified campaign costs:** Actual campaigns may include discounts, service costs, contact costs, and other expenses.
6. **No causal uplift estimation:** Churn probability alone cannot establish whether a customer will respond to an offer.
7. **No uncertainty intervals:** The estimates do not quantify uncertainty in retention lift, CLV, or costs.

A randomized controlled campaign or a suitable quasi-experimental evaluation with treatment and control groups would be needed to estimate campaign effectiveness more reliably.

---

## Conclusion

Notebook 09 connects customer churn-risk predictions and CLV estimates with hypothetical retention campaign economics. It produces scenario-based estimates of campaign cost, potential benefit, net benefit, ROI, and break-even retention lift.

The results provide a foundation for business planning and the final project report, while making clear that actual campaign effectiveness and financial returns must be validated with real retention campaign data.
