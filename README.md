

# 💳 FinTech Innovations — Loan Approval Predictive Model

## 📌 Project Overview

FinTech Innovations partners with traditional banks to **modernize the loan approval process**, which historically relied on manual reviews. Manual approvals often lead to inconsistent decisions, delays, and potential loss of profitable customers.

This project implements a **machine learning–driven decision support system** to:

* Standardize risk assessment
* Minimize financial losses due to false approvals
* Improve efficiency and fairness in loan approvals

The solution combines **classification and regression models** to predict both **loan approval decisions** and **applicant risk scores**, using a cost-sensitive evaluation framework aligned with business priorities.

---

## 🎯 Business Context

* **Current Challenges:** Manual review introduces bias, inconsistency, and slow processing.
* **Stakeholders:** Loan officers, risk analysts, bank executives.
* **Implications of Model Errors:**

  * False Positives (approving risky loans) → high financial loss (~$8,000 per bad loan)
  * False Negatives (rejecting good applicants) → missed revenue opportunities (~$8,000 per good loan denied)
* **Modeling Goals:** Minimize costly false approvals while maintaining a high approval rate.

---

## 🧠 Data Understanding

* **Dataset:** Applicant demographics, financial metrics, credit history, employment, loan purpose, and other financial indicators.
* **Key Observations:**

  * Class imbalance: ~75–80% loans not approved, 20–25% approved
  * Missing values in **MaritalStatus**, **EducationLevel**, and **SavingsAccountBalance** handled as “Unknown” or median imputation
  * Skewed financial features handled with robust scaling
* **Important Features:**

  * **Strong positive correlation with approval:** RiskScore, CreditScore, AnnualIncome, NetWorth
  * **Negative correlation:** InterestRate, RiskScore inverse, Debt-to-Income ratio
* **Feature Relationships:** Multicollinearity identified in highly correlated pairs (AnnualIncome ↔ MonthlyIncome, TotalAssets ↔ NetWorth, Experience ↔ Age)

---

## ⚙️ Data Preparation

* Created separate preprocessing pipelines for numeric, categorical, and ordinal features using **ColumnTransformer** and **Pipeline**
* Imputed missing values using median or “Unknown” labels
* Scaled numeric features where necessary for regression models
* Addressed class imbalance using **class weighting** and **stratified train-test splits**

---

## 🏗️ Modeling Approach

### Classification — Loan Approval

* **Algorithm:** Random Forest Classifier (best balance of accuracy and interpretability)
* **Performance:**

  * Accuracy: **99%**
  * Precision: **0.99**, Recall: **0.95** (approved loans)
  * Optimal Threshold: **0.65** (balances business cost and approval rate)
* **Cost-Sensitive Evaluation:**

  * False approvals minimized to reduce expected financial loss
  * Expected business cost: **$716,000**

### Regression — Risk Score Prediction

* **Algorithm:** Random Forest Regressor
* **Performance:**

  * R²: **0.994**
  * RMSE: **0.616**, MAE: **0.421**
* Predicted risk scores align closely with actual risk, enabling proactive decision-making

---

## 📊 Key Insights

* **Most impactful features:** RiskScore, Debt-to-Income Ratio, Annual & Monthly Income
* **Business Implications:**

  * Automate standard approvals, reducing workload for loan officers
  * Focus manual review on borderline applications
  * Provide explainable, regulatory-compliant decisions
* **Threshold Tuning:** Cost-aware threshold reduces expected losses while maintaining a high approval rate

---

## 📈 Evaluation & Visualization

* **Classification:** Confusion matrix, ROC-AUC, Precision-Recall curves
* **Regression:** Predicted vs. Actual scatter plots, feature importance visualization
* **Interpretability:** Feature importance aligns with financial intuition, supporting explainable AI practices

---

## 💡 Recommendations

* Review potential target leakage features (RiskScore, MonthlyLoanPayment, Debt-to-Income)
* Monitor model over time with new applicants to ensure robustness
* Consider ensemble models for incremental improvements
* Continue using cost-sensitive thresholds for business-aligned decision-making

---

## 🛠️ Tech Stack

* **Python**
* **Scikit-learn** (Random Forest, preprocessing, evaluation)
* **Pandas & NumPy** (data manipulation)
* **Matplotlib & Seaborn** (visualizations)
* **Jupyter Notebook** (analysis & reporting)

---

## 🏦 Business Impact

* Standardized loan approval decisions
* Reduced financial losses from bad approvals (~27% improvement over manual baseline)
* Improved operational efficiency and fairness
* Supports regulatory compliance through model explainability






