# Customer Churn Prediction & Retention Strategy

## Project Overview

This project focuses on predicting customer churn and developing proactive retention strategies as part of the Telkom × RevoU Virtual Internship. Using customer behavior, network quality, payment behavior, usage patterns, and complaint data, the analysis identifies customers at risk of churn and the factors contributing to the model's predictions.

The project applies machine learning classification models and SHAP explainability to support risk-based customer prioritization and targeted retention interventions.

**Project Duration:** October 2026

---

## Business Problem

Customer retention efforts are often reactive, with customers generally approached after submitting a cancellation request. This limits the opportunity to identify at-risk customers before they decide to leave.

How can machine learning predict customers with a higher likelihood of churn and help the business prioritize proactive retention strategies?

---

## Objectives

- Analyze customer characteristics and behavioral patterns associated with churn.
- Develop and compare machine learning classification models to predict customer churn.
- Evaluate model performance using relevant classification metrics.
- Identify key churn prediction drivers using feature importance and SHAP explainability.
- Identify high-risk customers and recommend targeted retention strategies.

---

## Analytical Approach

The analysis follows an end-to-end machine learning workflow:

**Data Understanding → Data Quality Assessment → Data Preparation → Exploratory Data Analysis → Feature Engineering → Model Development → Model Evaluation → SHAP Explainability → Business Recommendations**

### 1. Data Understanding & Preparation

- Reviewed training and test datasets containing 20,000 and 4,000 customers, respectively.
- Assessed missing values, duplicates, data types, identifier uniqueness, categorical values, and logical data ranges.
- Prepared features and target labels for churn classification.
- Performed feature engineering and categorical encoding to ensure consistent model inputs.

### 2. Exploratory Data Analysis

- Analyzed churn patterns across customer characteristics, payment behavior, complaints, network quality, and usage activity.
- Compared observed churn rates across customer groups to identify potential risk indicators.
- Examined customer activity, usage ratio, and payment personas to understand differences between churned and active customers.

### 3. Model Development & Evaluation

- Developed and compared Logistic Regression, Random Forest, and XGBoost classification models.
- Optimized model hyperparameters using GridSearchCV and RandomizedSearchCV.
- Evaluated model performance using accuracy, precision, recall, F1-score, ROC-AUC, and cross-validation.
- Selected XGBoost as the final model based on overall validation and cross-validation performance.

### 4. Feature Importance & Explainability

- Examined feature importance to identify variables contributing to churn predictions.
- Applied SHAP to interpret the direction and contribution of individual features to model predictions.
- Analyzed high-risk customers to identify their strongest prediction drivers and support targeted retention strategies.

### 5. Test Prediction & Risk Prioritization

- Generated churn predictions and churn probabilities for 4,000 test customers.
- Applied a probability threshold of 50% to identify customers classified as high-risk.
- Grouped high-risk customers by their strongest SHAP drivers to support more targeted retention interventions.

---

## Key Findings

### 1. Churn Patterns from EDA

- Customers in the lowest network quality group (0–60) recorded an observed churn rate of **96.40%**.
- Customers in the low active-days group recorded an observed churn rate of **29.05%**.
- Customers classified under the late-payment persona recorded an observed churn rate of **35.07%**.
- Customers in the low usage-ratio group recorded an observed churn rate of **31.48%**.

### 2. Model Performance

XGBoost was selected as the final model based on overall validation and cross-validation performance.

| Model | Accuracy | Precision | Recall | F1-Score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 96.90% | 93.40% | 74.25% | 82.73% | 96.43% |
| Random Forest | 97.30% | 93.98% | 78.00% | 85.25% | 96.85% |
| XGBoost | 97.20% | 92.60% | 78.25% | 84.82% | 97.19% |

- XGBoost achieved the highest validation ROC-AUC at **97.19%**.
- It also achieved the highest recall at **78.25%** among the compared models.
- Cross-validation ROC-AUC reached **97.83%**, supporting the model selection.

### 3. Key Drivers of Churn Prediction

SHAP analysis highlighted the following important contributors to churn predictions:

- **Network quality:** `avg_quality_3m` was among the most influential features.
- **Payment behavior:** `avg_late_payment_days_6m` contributed to higher predicted churn risk.
- **Customer activity and usage:** lower active days and usage ratio tended to push predictions toward churn.
- **Complaints:** higher `complaint_count_6m` tended to increase predicted churn risk.

SHAP values describe feature contributions to model predictions and should not be interpreted as proof of causal relationships.

### 4. High-Risk Customer Identification

- The model identified **324 high-risk customers** out of 4,000 test customers.
- These customers represented **8.10%** of the test dataset and met the predicted churn probability threshold of at least 50%.
- Network quality was the strongest SHAP driver for **287 of the 324 high-risk customers (88.58%)**.
- Payment delays, complaints, late-payment frequency, and active days were the strongest drivers for the remaining high-risk customers.

---

## Business Recommendations

- **Prioritize high-risk customers:** Focus retention efforts on the 324 customers with predicted churn probabilities of at least 50%.
- **Address network quality issues:** Prioritize network investigation and service recovery for high-risk customers whose predictions are strongly influenced by network quality.
- **Provide targeted interventions:** Match retention actions to individual risk drivers, including payment support, faster complaint resolution, and customer re-engagement.
- **Develop targeted retention campaigns:** Use churn probabilities and customer risk profiles to prioritize appropriate retention offers and outreach.
- **Operationalize proactive retention:** Implement periodic customer scoring, high-risk customer identification, driver-based interventions, and outcome monitoring.
- **Monitor model performance:** Reassess prediction quality and retention outcomes as new customer data becomes available.

---

## Tools

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- SHAP
- Matplotlib
- Seaborn
- Google Colab
- Machine Learning
- Exploratory Data Analysis (EDA)

---

## Project Files

| File | Description |
|---|---|
| `analysis/` | Python notebook covering data quality assessment, EDA, feature engineering, model development, evaluation, SHAP explainability, and test predictions |
| `presentation/` | Project presentation covering business context, analytical findings, model performance, and retention recommendations |

---

## Disclaimer

This project was developed for educational and portfolio purposes as part of the Telkom × RevoU Virtual Internship. The dataset is a synthetic representation and does not reflect actual Telkom Indonesia customer data, operational performance, financial information, or business conditions. Model predictions and recommendations should not be interpreted as actual business results.
