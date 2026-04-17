# 💳 Payment Fraud Detection

A machine learning project that detects fraudulent online payment transactions using multiple classification algorithms — Logistic Regression, Decision Tree, and Neural Network.

---

## 📁 Dataset

- **File:** `online_payments_fraud_detection_dataset.csv`
- **Target:** `isFraud` (binary: 0 or 1)
- **Class Distribution:**
  - Not Fraud: ~99.87%
  - Fraud: ~0.13% *(heavily imbalanced dataset)*

> 🔒 Dataset is not included in this repository. Provided by faculty for academic purposes only.

---

## 🔄 Project Pipeline

### 1. Exploratory Data Analysis
- Inspected shape, data types, numerical and categorical features
- Analyzed variance, skewness, and feature distributions
- Visualized class imbalance with a bar chart

### 2. Data Preprocessing
- **No missing values** — no imputation needed
- **Dropped irrelevant columns:** `nameOrig`, `nameDest` (noise), `isFlaggedFraud` (target leakage)
- **Dropped correlated columns:**
  - `newbalanceOrig` (perfect correlation with `oldbalanceOrg`)
  - `newbalanceDest` (near-perfect correlation with `oldbalanceDest`)
- Visualized correlations using a heatmap

### 3. Encoding
- `type` column (categorical) encoded using `LabelEncoder`

### 4. Feature Scaling
- Applied `RobustScaler` — chosen for its resilience to outliers in financial data
- Decision Tree skips scaling as it is not required

### 5. Train/Test Split
- 70% training / 30% testing
- `random_state=1` for reproducibility

### 6. Models Trained
- **Logistic Regression** (`max_iter=5000`)
- **Decision Tree**
- **Neural Network / MLP** (`hidden_layer_sizes=(100,)`, `activation='relu'`, `solver='adam'`)

### 7. Evaluation
- Confusion Matrix
- Accuracy, Precision, Recall, F1 Score
- ROC Curve & AUC comparison across all models
- Classification Report

---

## 📊 Results

| Model | Accuracy | Precision (Fraud) | Recall (Fraud) | F1 Score (Fraud) |
|-------|----------|-----------|--------|----------|
| Logistic Regression | 99.93% | 82% | 3% | 6% |
| Decision Tree | 99.94% | 75% | 76% | 75% |
| Neural Network | 99.95% | 93% | 69% | 79% |

> ⚠️ Accuracy is misleading here due to severe class imbalance (~99.87% non-fraud).

> Metrics above focus on the **Fraud class (1)** which is what matters.

> Neural Network performs best overall with the highest precision (93%) and a strong F1 (79%).

> Logistic Regression fails almost entirely at detecting fraud — only 3% recall despite high accuracy.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| `pandas` | Data loading & manipulation |
| `seaborn` | Correlation heatmap visualization |
| `matplotlib` | Charts and plots |
| `scikit-learn` | Preprocessing, modeling, evaluation |

---

## 📂 Project Structure

```
payment-fraud-detection/
├── payment_fraud_detection_AI_model.ipynb   # Main notebook
├── online_payments_fraud_detection_dataset.csv  # Not included — faculty dataset
└── README.md
```