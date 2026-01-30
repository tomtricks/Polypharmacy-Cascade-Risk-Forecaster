# Polypharmacy Cascade Risk Forecaster  
**Databricks Capstone Project – 14 Days AI Challenge**

## Overview
This project builds a healthcare decision-support system that predicts the **future risk of adverse events caused by polypharmacy** (use of multiple medications).  
The system is designed to forecast risk up to **28 days ahead**, helping healthcare teams identify patients who may require early intervention.

This is a **risk forecasting and decision-support project**, not a medical device.

---

## Problem Statement
Polypharmacy often leads to cascading adverse events such as dizziness, falls, and fractures. These risks are difficult to detect early using static rules due to complex medication interactions.

The goal of this project is to use machine learning to:
- Predict patient-level adverse event risk
- Convert predictions into actionable risk categories
- Support proactive clinical decision-making

---

## Architecture Overview
The system is implemented using the **Databricks Lakehouse architecture**:

- **Bronze Layer**: Raw ingestion of patients, prescriptions, and events data  
- **Silver Layer**: Cleaned, joined, and standardized datasets  
- **Gold Layer**: Feature-engineered, ML-ready tables with risk outputs  

Machine learning is trained directly from Gold tables and predictions are written back to the database.


---

## Machine Learning Approach
- **ML Task**: Binary classification with probabilistic output
- **Model**: Logistic Regression (PySpark ML)
- **Why This Model**:
  - Interpretable
  - Suitable for healthcare risk scoring
  - Works well with limited features and noisy data

### Evaluation
- **Metric Used**: AUC-ROC
- **Result**: AUC = 0.59

This score reflects moderate predictive power, which is expected given public data limitations. The model is intended for **risk prioritization**, not diagnosis.

---

## Risk Stratification
Predicted probabilities are mapped into actionable risk categories:
- **High Risk (Red)**: Probability ≥ 0.70
- **Medium Risk (Amber)**: 0.40 – 0.70
- **Low Risk (Green)**: < 0.40

This enables clear decision support for monitoring and intervention planning.

---

## Business Impact
The system helps:
- Clinicians prioritize high-risk patients
- Hospitals reduce preventable adverse events
- Safety teams move from reactive to proactive care

Even modest predictive improvements can lead to meaningful operational benefits.

---

## Assumptions & Limitations
- Uses public healthcare datasets (not real-time hospital systems)
- Risk thresholds are heuristic
- No clinical validation is implied

---

## Reproducibility
All steps are implemented using:
- Databricks Community Edition
- PySpark & Spark SQL
- Delta Lake tables

Notebooks are organized by:
- Data ingestion
- Transformation
- Feature engineering
- Model training and evaluation

---
## References:
- [Architecture Diagram](assets/Architecture_FLow.png)
- [Dashboard Screenshot](assets/Dashboard.png)
- [Job pipeline](assets/Job_run.png)
- [ML FLow](assets/Logistic_regression_Graph.png)

---

## Disclaimer
This project is for educational and research purposes only and is **not intended for clinical use**.
