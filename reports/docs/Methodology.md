# Methodology

## Overview

This methodology aligns directly with the evaluation criteria for predictive maintenance using the NASA C-MAPSS dataset. It ensures that the project meets high standards in prediction accuracy, explainability, scientific rigor, and stakeholder usability through structured, goal-driven phases.

---

## Literature Review

* **Scope definition:** Establish the relevance of predictive maintenance in aviation and industrial contexts.
* **Dataset precedent:** Review key papers using the C-MAPSS dataset (e.g., Saxena & Goebel, 2008) for RUL estimation.
* **Modeling strategies:** Summarize and contrast traditional (e.g., regression trees, SVMs) and modern approaches (e.g., LSTM, Transformer models).
* **Feature extraction:** Highlight research on sensor fusion, temporal feature engineering, and degradation modeling.
* **Evaluation metrics:** List and justify MAE, RMSE, sMAPE, and classification-based metrics as standards in the field.
* **Explainability:** Explore SHAP, LIME, and feature importance methods used in recent maintenance models.
* **Gaps identified:** Emphasize the lack of reproducible, interpretable dashboards in real-world deployments.

**Deliverables:**
- `reports/documentation/Literature_Review.md`
- `reports/documentation/Evaluation_Criteria.md`

---

## 1. Data Acquisition and Understanding

* **Download and load** all four FD subsets (FD001–FD004) from NASA’s Prognostics Center.
* **Assess structure** of data: sensors, operational settings, cycle information.
* **Initial checks:** Missing values, data types, sensor signal quality.

**Deliverables:**
- `data/raw/` — Original NASA datasets
- `notebooks/0_data_overview.ipynb`

---

## 2. Exploratory Data Analysis (EDA) and Dashboard

* **Trend discovery:** Plot RUL trends, cycle distributions, and degradation patterns.
* **Sensor behavior:** Identify at least 3 sensors with predictive or monotonic signals.
* **Correlation analysis:** Quantify relationships between sensors and RUL.
* **Dashboard development:** Build an interactive dashboard that:

  * Filters by engine, sensor, and time.
  * Overlays RUL predictions and failure zones.
  * Presents clear and interpretable visualizations.

**Deliverables:**
- `reports/EDA/eda_summary.ipynb`
- `reports/figures/` — All generated plots
- `src/dashboard/dashboard_app.py`
- `notebooks/1_eda.ipynb`

---

## 3. Data Preprocessing

* **Labeling:**

  * RUL = max(cycle) - current cycle
  * Binary classification label = 1 if RUL ≤ 30 cycles, else 0
* **Normalization:** Per-sensor standardization
* **Feature selection:** Remove low-variance and redundant features
* **Sliding windows:** Optional for deep learning models

**Deliverables:**
- `src/preprocessing/preprocessing_pipeline.py`
- `data/processed/` — Cleaned and labeled datasets
- `notebooks/2_preprocessing.ipynb`

---

## 4. Feature Engineering

* **Descriptive features:** Rolling stats (mean, std), gradients, and deltas
* **Domain-specific insights:** Rate-of-change metrics, event counters
* **Dimensionality reduction:** Use PCA or autoencoders for sensor synthesis
* **Model interpretability setup:** Prepare for SHAP, feature importances

**Deliverables:**
- `src/preprocessing/feature_engineering.py`
- `notebooks/3_features.ipynb`

---

## 5. Modeling Phase

### 5.1 RUL Prediction (Regression)

* **Model types:** Linear Regression, Gradient Boosting, Random Forests, LSTM, Transformer
* **Evaluation Metrics:** MAE, RMSE, sMAPE, R²
* **Goal:** Achieve MAE < 20 cycles and R² > 0.70
* **Validation strategy:** Time-aware or grouped cross-validation to avoid leakage

### 5.2 Imminent Failure Classification

* **Objective:** Predict whether an engine will fail within next N cycles (e.g., 30)
* **Model types:** Logistic Regression, XGBoost, Random Forest, LSTM
* **Evaluation Metrics:** Precision, Recall, F1, ROC-AUC, PR-AUC
* **Goal:** F1-score > 0.80, ROC-AUC > 0.85

### Deliverables:

- `src/modeling/rul_model.py`
- `src/modeling/failure_classifier.py`
- `models/` — Saved model weights
- `notebooks/4_modeling.ipynb`

---

## 6. Model Evaluation and Selection

* **Metric comparison:** Select models that meet or exceed Acceptable targets
* **Robustness tests:** Evaluate model on multiple FD subsets
* **Error diagnostics:** Examine false positives/negatives and high-error engines

**Deliverables:**
- `src/evaluation/evaluation_metrics.py`
- `reports/figures/error_analysis/`
- `notebooks/5_evaluation.ipynb`

---

## 7. Explainability and Scientific Validity

* **SHAP values and feature importance** to explain model decisions
* **Partial Dependence Plots (PDP)** and sensor trend overlays
* **Documentation:** Scientific rationale behind selected features and models

**Deliverables:**
- `src/evaluation/explainability.py`
- `reports/figures/shap/`
- `notebooks/6_explainability.ipynb`

---

## 8. Deployment and Usability

* **Integrated dashboard:** Combine model outputs with EDA for end-users
* **Cycle-level predictions:** RUL and failure probabilities
* **Visual overlays:** Failure zone markers and confidence indicators
* **Non-technical use:** Ensure dashboard insights are interpretable by stakeholders

**Deliverables:**
- `src/dashboard/dashboard_app.py` (e.g., Streamlit)
- `reports/EDA/dashboard_walkthrough.md`
- `models/final_models/` — Exported model artifacts

---

## 9. Reproducibility and Reporting

* **Reproducible pipeline:** One-click execution from raw data to results
* **Environment files:** Conda or pip + requirements.txt
* **Code organization:** Modular, documented, version-controlled scripts
* **Final report:** Summarize insights, metrics, limitations, and next steps

**Deliverables:**
- `requirements.yml` — Conda env
- `README.md` — Project overview
- `docs/Methodology.md`
- `docs/Problem_Statement.md`
- `reports/final_report.pdf` or `.md`

---

## 10. REST API for Model Serving

**Objective:** Make predictions available to external systems in real-time.

**Framework:** Use FastAPI (or Flask) to serve RUL and classification models.

**Endpoints:**
* /predict/rul — Accepts input features and returns RUL estimate
* /predict/failure — Returns binary failure classification
* /health — Basic endpoint for monitoring service status

**Design considerations:**
* Input validation, error handling, and response time optimization
* Containerization (Docker) for scalable deployment
* Integration with logging and monitoring tools (e.g., Prometheus, Grafana)

**Outcome:** A lightweight, production-ready REST API for seamless integration with dashboards, IoT platforms, or maintenance systems.

**Deliverables:**
- `app/main.py` — FastAPI or Flask app
- `app/routes/predict_rul.py`, `predict_failure.py`
- `Dockerfile` (optional)
- `docs/API_Usage.md` — Sample requests