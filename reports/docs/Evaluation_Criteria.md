# Evaluation Criteria

## Overview

This document outlines the formal criteria for evaluating the success of the project "Predictive Maintenance of Jet Engines Using the NASA C-MAPSS Dataset." The project includes two primary machine learning tasks: regression to estimate Remaining Useful Life (RUL) and classification to detect proximity to engine failure. In addition, success includes producing scientifically meaningful exploratory analysis and building a dashboard for stakeholder use.

---

## Task 1: RUL Prediction (Regression)

### Goal

Predict the Remaining Useful Life (RUL) for each engine at any time step using historical sensor and operational data.

### Metrics

* **Mean Absolute Error (MAE)**
* **Root Mean Square Error (RMSE)**
* **Symmetric Mean Absolute Percentage Error (sMAPE)**
* **R² (Coefficient of Determination)**

### Target Values

| Metric | Acceptable  | Excellent   |
| ------ | ----------- | ----------- |
| MAE    | < 20 cycles | < 10 cycles |
| RMSE   | < 25 cycles | < 15 cycles |
| sMAPE  | < 25%       | < 15%       |
| R²     | > 0.70      | > 0.85      |

---

## Task 2: Failure Classification (Binary)

### Goal

Classify whether an engine is within a critical failure window (e.g., fails within the next 30 cycles).

### Metrics

* **Precision**
* **Recall**
* **F1-Score**
* **ROC-AUC**
* **PR-AUC**

### Target Values

| Metric    | Acceptable | Excellent |
| --------- | ---------- | --------- |
| Precision | > 0.80     | > 0.90    |
| Recall    | > 0.75     | > 0.90    |
| F1-Score  | > 0.80     | > 0.90    |
| ROC-AUC   | > 0.85     | > 0.95    |
| PR-AUC    | > 0.80     | > 0.90    |

---

## Exploratory Data Analysis (EDA) & Dashboard

### Goals

* Reveal degradation trends in sensor readings
* Identify significant predictors of failure and RUL
* Present findings in an interactive and understandable dashboard

### Success Criteria

| Aspect                  | Signal of Success                                          |
| ----------------------- | ---------------------------------------------------------- |
| Sensor Insights         | Identify 3+ sensors with monotonic or predictive behavior  |
| Feature Correlation     | Detect 5+ features correlated with RUL or failure          |
| Dashboard Interactivity | Enable filtering by engine, time, sensor, and failure zone |
| Visualization Quality   | Time-series, RUL overlays, failure zone markers            |
| Stakeholder Use         | Domain users can interpret results without code access     |

---

## Scientific Validity & Generalizability

### Goals

Ensure the project is scientifically sound, reproducible, and explainable.

### Criteria

| Aspect           | Requirement                                                   |
| ---------------- | ------------------------------------------------------------- |
| Reproducibility  | Pipeline runs end-to-end from raw data to results             |
| Validation       | Employs time-aware validation or cross-validation             |
| Explainability   | Uses SHAP, feature importance, or PDPs for model transparency |
| Generalizability | Trained models tested across FD001–FD004 scenarios            |

---

