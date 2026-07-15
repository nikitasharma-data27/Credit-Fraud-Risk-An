# Credit Card Transaction Fraud Detection & Risk Analysis

A business-analyst-oriented fraud risk project: exploratory analysis, a risk-scoring model, and business recommendations a risk/product team could actually act on.

> **Data note:** Uses a synthetically generated transaction dataset (50,000 records) modeled on publicly documented fraud characteristics (late-night timing, distance-from-home anomalies, high-risk merchant categories, newer accounts). No real financial or customer data is used.

---

## Business Problem

Card issuers face two costly failure modes:

- Undetected fraud (direct loss)
- False alarms on legitimate transactions (customer friction, support cost, churn risk)

This project asks:

> Which transaction signals best separate fraud from legitimate activity, and how should a business balance the tradeoff between the two error types?

---

## What's in this repo

| File | Description |
|------|-------------|
| `credit.ipynb` | Full analysis notebook -- EDA, model, evaluation, business recommendations |
| `transactions.csv` | Synthetic dataset (50,000 transactions) |
| `Fraud_Analysis_Explained` | Standalone script to regenerate the dataset |

---

## Key Findings

- Fraud rate: ~1.7% of transactions
- Peak fraud window: 12am-5am, roughly 5x the daytime baseline
- Entertainment and Jewelry categories show the highest fraud concentration
- Fraudulent transactions average ~13x higher amounts and occur far from the cardholder's home compared to legitimate activity

---

## Model

Logistic regression risk-scoring model (chosen for interpretability), tuned for recall over raw accuracy given the class imbalance.

### Performance

- Recall: **97.1%** (catches nearly all fraud in the test set)
- ROC-AUC: **0.998**
- Precision-recall tradeoff analyzed explicitly, since threshold selection is a business decision (fraud loss vs. customer friction), not a purely technical one.

---

## Business Recommendations

- Step-up verification for late-night transactions
- Dynamic flagging for high-distance-from-home transactions
- Category-specific monitoring for Entertainment and Jewelry
- Tunable risk threshold set jointly with risk/CX teams, not a fixed default
- Treat as a baseline model -- production systems would likely add ensemble methods and transaction-velocity features

---

## Tools

Python (Pandas, NumPy, scikit-learn, Matplotlib, Seaborn), Logistic Regression, EDA, Risk Scoring, Precision-Recall Analysis
