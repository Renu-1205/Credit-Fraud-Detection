## Project Overview

This project builds a **production-ready fraud detection system** for credit card transactions using machine learning. The model identifies fraudulent transactions with **84.5% precision** and **81.5% recall**, making it suitable for real-world deployment.

### Key Results

| Metric | Value |
|--------|-------|
| **Precision** | 84.5% (±2.5%) |
| **Recall** | 81.5% (±2.4%) |
| **F1 Score** | 0.829 (±0.02) |
| **False Positives** | ~15 per 56,000 transactions |
| **Missed Frauds** | ~18 per 98 frauds |


---

## 📁 Dataset

**Source**: [Kaggle Credit Card Fraud Detection](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

| Property | Value |
|----------|-------|
| Total Transactions | 284,807 |
| Fraud Cases | 492 (0.17%) |
| Non-Fraud Cases | 284,315 (99.83%) |
| Features | 31 (Time, V1-V28, Amount, Class) |

### Class Imbalance
No Fraud: ████████████████████████████████████████ 99.83%

Fraud: █ 0.17%


**Note**: Features V1-V28 are already PCA-transformed for confidentiality.

---

## 🏆 Best Model

**Calibrated XGBoost Classifier** with threshold = 0.5

### Model Configuration
model = xgb.XGBClassifier(
    scale_pos_weight=577.9,  # Accounts for class imbalance
    learning_rate=0.1,
    n_estimators=100,
    max_depth=4,
    random_state=42
)

┌─────────────────────────────────────────────────────────┐
│  Precision: 84.5% (±2.5%)                              │

│  Recall:    81.5% (±2.4%)                              │

│  F1 Score:  0.829 (±0.02)                              │
└─────────────────────────────────────────────────────────┘
