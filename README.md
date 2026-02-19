# Dynamic Credit Line Adjustment System

## Overview

This project builds an end-to-end Credit Risk Modeling framework to dynamically adjust credit limits based on predicted borrower risk.

Using ~1.3 million historical loan records, a Probability of Default (PD) model was developed and integrated into a rule-based credit exposure strategy to reduce portfolio Expected Loss (EL).

The project follows the CRISP-DM methodology and simulates a realistic credit risk lifecycle including modeling, strategy design, deployment simulation, and monitoring.

---

## Business Objective

Financial institutions extend revolving credit to borrowers with varying risk profiles. Static credit limits can expose lenders to excessive losses from high-risk borrowers.

The objective of this project is to:

- Build a Probability of Default (PD) model
- Segment borrowers into risk buckets
- Dynamically adjust credit limits based on predicted risk
- Reduce portfolio-level Expected Loss (EL)

---

## Credit Risk Framework

Expected Loss is calculated as:

EL = PD × LGD × EAD

Where:
- PD = Probability of Default (modeled)
- LGD = Loss Given Default (assumed 60%)
- EAD = Exposure at Default (approximated using revolving credit limit)

---

## Methodology (CRISP-DM)

### 1. Business & Data Understanding
- Defined default target (Charged Off = 1, Fully Paid = 0)
- Removed leakage variables
- Cleaned and standardized dataset
- Engineered foundational features

### 2. Exploratory Data Analysis
- Analyzed class imbalance
- Evaluated default rate by feature bins
- Identified key risk drivers
- Assessed multicollinearity via correlation matrix

### 3. PD Model Development
- Logistic Regression with Pipeline & ColumnTransformer
- Stratified train-test split
- Cross-validation using ROC-AUC

Model Performance:
- AUC ≈ 0.71
- Monotonic decile default rate separation
- Probability calibration verified

### 4. Risk Segmentation & Policy Simulation
- Borrowers segmented into risk buckets
- Rule-based credit limit multipliers applied
- Baseline Expected Loss calculated
- Adjusted Expected Loss recalculated

Result:
- ~18% reduction in portfolio Expected Loss
- Reduction in weighted portfolio PD

### 5. Deployment & Monitoring Simulation
- Model saved using joblib
- Real-time scoring workflow implemented
- AUC monitoring simulated
- Population Stability Index (PSI) implemented for drift detection

---

## Key Results

- Model AUC: ~0.71
- Decile monotonicity achieved
- Calibration aligned with observed default rates
- ~18% portfolio Expected Loss reduction
- Dynamic credit limit strategy successfully simulated

---

## Repository Structure

dynamic-credit-line-adjustment/
│
├── notebooks/
│   ├── 01_business_data_understanding.ipynb
│   ├── 02_exploratory_data_analysis.ipynb
│   ├── 03_pd_modeling_and_simulation.ipynb
│
├── pd_model.pkl
├── requirements.txt
└── README.md

---

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn
- Joblib

---

## Limitations

- LGD assumed constant at 60%
- EAD approximated using revolving credit limit
- No macroeconomic variables included
- No out-of-time validation performed
- No profitability modeling (interest income impact not included)

---

## Future Improvements

- Out-of-time validation
- Profitability optimization (Risk-adjusted return modeling)
- Challenger models (e.g., Gradient Boosting)
- Behavioral feature engineering
- Macro-adjusted PD modeling

---

## Resume Highlight

Developed an end-to-end Probability of Default (PD) model on 1.3M+ loan records using CRISP-DM methodology; achieved AUC ~0.71 with monotonic decile separation and calibrated probabilities. Designed a dynamic credit limit adjustment strategy reducing portfolio Expected Loss by ~18%.

---

## Conclusion

This project demonstrates how predictive modeling can directly inform credit strategy and improve portfolio-level risk management through a data-driven decision framework.
