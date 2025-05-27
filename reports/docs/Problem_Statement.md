# Problem Statement

## Project Title

**Predictive Maintenance of Jet Engines Using the NASA C-MAPSS Dataset**

## Background

Jet engines undergo gradual wear and degradation during operation. Failures can be catastrophic and costly, which makes predictive maintenance crucial for aviation safety and efficiency. Traditional maintenance schedules are time-based, not condition-based, potentially leading to premature servicing or unexpected failures.

The NASA C-MAPSS (Commercial Modular Aero-Propulsion System Simulation) dataset simulates engine degradation over time under various operating conditions and fault modes. It provides time-series sensor data for multiple engine units until failure, creating a valuable benchmark for developing prognostics and health management (PHM) systems.

## Objective

The objective of this project is to design and implement a data analytics and machine learning pipeline that leverages the C-MAPSS dataset to:

### Primary Task

* Predict the **Remaining Useful Life (RUL)** of jet engines at each operational cycle.

### Secondary Task

* Detect whether an engine is approaching failure within a specified critical time window (e.g., within the next 30 cycles).

## Inputs

* Time-series data for each engine unit

  * Sensor measurements (21 sensors)
  * Operational settings (3 variables)
  * Engine ID and cycle number
* Ground truth: known failure cycle for each engine unit

## Outputs

* Numeric RUL prediction for each cycle of each engine
* Binary classification of imminent failure risk (e.g., 1 if RUL ≤ 30, else 0)
* Interactive EDA dashboard showing sensor trends, RUL predictions, and classification states

## Challenges

* High dimensionality and redundancy in sensor readings
* Irregular degradation trends across engines and operating conditions
* Time-series feature engineering and model generalization
* Interpretability of model predictions in a safety-critical context

## Scientific Contribution

This project provides a rigorous, reproducible workflow for PHM, demonstrating:

* Application of EDA to uncover degradation signals
* Advanced ML models for regression and classification on time-series data
* Visualization of model outputs in a decision-support dashboard
* Generalizability of findings across varying engine conditions and datasets (FD001–FD004)

## Scope

The project is restricted to the publicly available C-MAPSS datasets and does not include real-time deployment or integration with onboard systems. However, all results and code will be suitable for extension to real-world PHM systems.
