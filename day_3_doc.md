# Notebook 04 — LightGBM Churn Prediction

## 1. Overview

This notebook builds a machine learning model using **LightGBM (Light Gradient Boosting Machine)** to predict customer churn in the CHURNIQ — Customer Lifetime Value and Churn Intelligence System.

The model uses the prepared training and testing datasets from the previous notebook to learn customer behavior patterns and predict whether a customer is likely to leave the telecom service.

## 2. Objectives

- Load the prepared training and testing datasets.
- Train a LightGBM classification model.
- Build a reusable machine learning pipeline.
- Generate churn predictions and prediction probabilities.
- Evaluate model performance using classification metrics.
- Save the trained pipeline and evaluation results for future use.
- Prepare the model for SHAP explainability in Notebook 05.

## 3. Input Files

The notebook uses the following files from the `models` directory:

| File | Purpose |
|---|---|
| `X_train.csv` | Training features |
| `X_test.csv` | Testing features |
| `y_train.csv` | Training churn labels |
| `y_test.csv` | Testing churn labels |

These files were generated during the feature engineering and model preparation stage.

## 4. Model and Evaluation

**Algorithm:** LightGBM Classifier

LightGBM is a gradient boosting algorithm that builds decision trees sequentially, with each new tree helping improve the model's predictions.

The notebook evaluates the model using relevant classification metrics:

- **ROC-AUC:** Measures the model's ability to distinguish between churners and non-churners across classification thresholds.
- **Average Precision:** Summarizes precision-recall performance, particularly useful when churn classes are imbalanced.
- **Additional classification metrics:** Accuracy, precision, recall, F1-score, and a confusion matrix, if calculated in the notebook.

Actual metric values should be taken from the notebook's evaluation output.

## 5. Output Files

The notebook saves its reusable model and evaluation results in the `../models/` directory.

| File | Description |
|---|---|
| `churniq_lightgbm_pipeline.joblib` | Saved fitted LightGBM pipeline |
| `lightgbm_metrics.csv` | Saved model evaluation metrics |

The saved pipeline can be loaded in later notebooks without retraining the model, provided the required dependencies and compatible environment are available.

## 6. Workflow

1. Load the prepared training and testing datasets.
2. Prepare the features and target labels.
3. Define and train the LightGBM pipeline.
4. Generate predictions on the test dataset.
5. Calculate evaluation metrics.
6. Save the fitted pipeline using Joblib.
7. Export evaluation metrics to CSV.
8. Pass the trained pipeline to Notebook 05 for SHAP analysis.

## 7. Why LightGBM?

- Efficient gradient boosting implementation.
- Captures nonlinear relationships and interactions between customer features.
- Suitable for structured, tabular datasets.
- Supports probability-based churn predictions.
- Can be explained using SHAP to investigate feature contributions.

## 8. Next Step

Notebook 05 — **Model Explainability with SHAP** — uses the saved pipeline to understand which customer characteristics influence churn predictions globally and for individual customers.

## Project

**CHURNIQ — Customer Lifetime Value and Churn Intelligence System**

The broader objective is to predict churn, understand the reasons behind customer attrition, and support data-driven retention decisions.
