# Dynamic Credit Line Adjustment System  
## Probability of Default (PD) Based Credit Risk Framework

## Project Overview

This project implements an end-to-end Probability of Default (PD) modeling framework and integrates it into a dynamic credit line adjustment system to simulate portfolio-level risk optimization.

The objective is to predict borrower default risk and adjust credit exposure accordingly to reduce overall portfolio Expected Loss.

The project follows the CRISP-DM methodology and covers data preparation, modeling, calibration, business simulation, and deployment thinking.

---

## Business Objective

Design a system that:

- Predicts borrower Probability of Default (PD)
- Segments customers into risk buckets
- Dynamically adjusts credit limits based on risk
- Reduces portfolio-level Expected Loss (EL)

---

## Dataset

- 1.3M+ loan records
- Binary target variable: `default`
- Financial and behavioral features including:
  - Credit utilization
  - FICO range
  - Interest rate
  - Loan purpose
  - Income
  - Delinquencies
  - Home ownership
  - Geographic state

---

## Methodology (CRISP-DM)

### 1. Business Understanding
Defined PD-driven exposure optimization as core objective.

### 2. Data Understanding & Preparation
- Removed leakage variables
- Handled outliers via winsorization
- Cleaned placeholder values
- Used ColumnTransformer for preprocessing
- Stratified train-test split

### 3. Modeling
- Logistic Regression (baseline PD model)
- Cross-validation using ROC-AUC
- Test AUC ≈ 0.71
- Solver: lbfgs
- Removed class_weight to ensure proper probability calibration

### 4. Model Evaluation
- Decile-based risk segmentation
- Verified monotonic increase in default rate
- Calibration analysis (Predicted PD ≈ Actual default rate)
- Confusion matrix evaluation
- Interpreted key risk drivers via model coefficients

### 5. Deployment Simulation
- Defined risk buckets (Very Low → Very High)
- Designed rule-based credit limit adjustment policy
- Simulated portfolio Expected Loss:

EL = PD × LGD × EAD

Assumptions:
- LGD = 60%
- EAD ≈ total revolving credit limit

---

## Key Results

- PD Model AUC: ~0.71
- Proper probability calibration achieved
- 18% reduction in simulated portfolio Expected Loss
- Reduction in weighted portfolio PD:
  - Before: 0.1785
  - After: 0.1557

This demonstrates effective exposure reallocation toward lower-risk borrowers.

---

## Key Risk Drivers Identified

- Higher interest rates increase default probability
- Small business loan purpose increases risk
- Mortgage ownership reduces risk
- Geographic factors influence default behavior

---

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Git & GitHub

---

## Project Structure

credit-line-adjustment-system/
│
├── notebooks/
│   └── pd_model_baseline.ipynb
│
├── README.md
└── .gitignore

---

## What This Project Demonstrates

- End-to-end credit risk modeling
- Proper handling of data leakage
- Probability calibration awareness
- Business-aligned metric selection
- Portfolio-level risk simulation
- Model interpretability and risk insights

---

## Future Improvements

- Hyperparameter tuning
- Challenger model (e.g., XGBoost)
- Revenue-risk tradeoff simulation
- Out-of-time validation
- Production-ready modular architecture

---

## Author

Rudransh Shukla  
B.Tech (IT) | Credit Risk Modeling & Data Science
