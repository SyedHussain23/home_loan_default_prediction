# 🏦 home_loan_default_prediction

This project predicts whether a **home loan applicant will default** using machine learning and multi-source financial data.

It demonstrates a realistic **credit risk modeling pipeline**, including:

* Multi-table data integration
* Missing value handling
* Feature engineering via aggregations
* Imbalanced classification handling
* Model comparison
* Cross-validation

The objective is to classify applicants into:

**0 → Non-Defaulter**
**1 → Defaulter**

---

## 📌 Project Overview

* **Problem Type:** Binary Classification
* **Domain:** Banking / Credit Risk Analytics
* **Target Variable:** `TARGET`
* **Dataset Size:** 300k+ applications with multiple relational tables
* **Models Used:** Logistic Regression, LightGBM

---

## 📊 Dataset

The dataset contains multiple relational tables describing customer credit history.

### Tables Used

* application_train.csv
* bureau.csv
* bureau_balance.csv
* credit_card_balance.csv
* POS_CASH_balance.csv
* installments_payments.csv
* previous_application.csv

Dataset Link:
[https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1006-HomeLoanDef.zip](https://d3ilbtxij3aepc.cloudfront.net/projects/CDS-Capstone-Projects/PRCP-1006-HomeLoanDef.zip)

---

## 🔍 Data Preprocessing

### Missing Value Handling

* Dropped columns with >50% missing values
* Median imputation for numerical features
* Mode imputation for categorical features

### Categorical Encoding

* One-hot encoding applied to categorical variables

### Data Integration

Aggregated relational tables using `groupby + aggregation` to enrich application data.

Examples:

* Bureau credit statistics
* Previous loan amounts and annuities

---

## ⚙️ Feature Engineering

* Aggregated credit history features
* Previous loan behavior indicators
* Handling infinite values
* Column name normalization
* Final dataset cleaned with median imputation

---

## ⚖️ Imbalanced Data Handling

The dataset contains significantly fewer defaulters.

Solution:

* Applied **scale_pos_weight** in LightGBM
* Evaluated using Recall and AUC-ROC instead of accuracy alone

---

## 🧠 Model Training

### Models Implemented

* Logistic Regression (baseline)
* LightGBM (gradient boosting)

Training setup:

* Stratified train-test split
* 3-fold Stratified Cross-Validation
* Reduced dataset size for faster experimentation

---

## 📈 Model Evaluation

### Logistic Regression

* Accuracy ≈ **0.92**
* Precision = **0.0**
* Recall = **0.0**
* F1-score = **0.0**
* AUC-ROC ≈ **0.65**

⚠️ Failed to detect defaulters

---

### LightGBM

* Accuracy ≈ **0.75**
* Precision ≈ **0.18**
* Recall ≈ **0.58–0.61**
* F1-score ≈ **0.27–0.28**
* AUC-ROC ≈ **0.74–0.75**

✅ Successfully detects high-risk customers

---

## 🏆 Best Model

**LightGBM** is recommended for production because:

* Strong recall for defaulters
* Stable AUC-ROC
* Better risk detection despite lower accuracy

Logistic Regression is suitable only as a baseline.

---

## 📊 Feature Importance

Top features were extracted using LightGBM importance scores to identify key risk indicators influencing default prediction.

---

## ⚠️ Challenges & Solutions

### High Missing Values

✔ Dropped heavily missing columns and applied imputation

### Multiple Data Sources

✔ Aggregated relational datasets using groupby statistics

### Categorical Variables

✔ One-hot encoding

### Imbalanced Target

✔ Used scale_pos_weight and focused on recall + AUC

### Long Training Time

✔ Reduced CV folds and dataset size

---

## 🛠️ Tech Stack

| Tool                 | Purpose           |
| -------------------- | ----------------- |
| Python               | Programming       |
| Pandas / NumPy       | Data processing   |
| Scikit-learn         | ML baseline       |
| LightGBM             | Gradient boosting |
| Matplotlib / Seaborn | Visualization     |
| Requests / Zipfile   | Dataset retrieval |
| Jupyter Notebook     | Experimentation   |

---

## 🚀 How to Run

```bash
git clone https://github.com/SyedHussain23/home_loan_default_prediction
cd home_loan_default_prediction
pip install -r requirements.txt
jupyter notebook home_loan_default_prediction.ipynb
```

---

## 🔮 Future Improvements

* Hyperparameter tuning
* SMOTE / advanced imbalance handling
* Feature selection techniques
* SHAP explainability
* Model deployment (API)
* Ensemble stacking

---

## 👨‍💻 Author

**Syed Hussain Abdul Hakeem**

* LinkedIn: [https://www.linkedin.com/in/syed-hussain-abdul-hakeem](https://www.linkedin.com/in/syed-hussain-abdul-hakeem)
* GitHub: [https://github.com/SyedHussain23](https://github.com/SyedHussain23)

---

## ⭐ Show Your Support

If you found this project useful, consider giving it a ⭐.
