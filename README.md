# Customer Churn Prediction

## Overview

This project uses machine learning to predict customer churn in the telecommunications industry. Customer churn occurs when a customer stops using a company's services.

The objective is to identify customers who are more likely to leave, understand the factors influencing churn predictions, and explore how a company could prioritize customer retention efforts.

## Business Problem

Customer churn can result in lost revenue and increased customer acquisition costs. Predicting churn risk can help businesses identify customers who may need additional attention and prioritize retention campaigns.

This project explores how machine learning can support these decisions using customer demographics, account information, subscribed services, and billing data.

## Dataset

The project uses the Telco Customer Churn dataset, which contains customer information, services, account details, and churn status.

- **Target variable:** `Churn`
- `0` — Customer stayed
- `1` — Customer churned

The dataset contains 7,043 customers and 21 columns.

## Project Workflow

### 1. Data Cleaning

- Removed the customer ID from the modeling features.
- Converted `TotalCharges` from text to numeric values.
- Handled 11 blank `TotalCharges` values by replacing them with zero, corresponding to customers with zero tenure.
- Encoded the target variable, `Churn`, as binary values.

### 2. Exploratory Data Analysis

Explored churn patterns across numerical and categorical variables.

Key observations included:

- Approximately 26.5% of customers churned.
- Month-to-month contracts had a substantially higher churn rate than longer-term contracts.
- Customers with shorter tenure tended to have higher churn rates.
- Higher churn rates were also observed among customers without online security or technical support.
- Tenure and total charges were strongly correlated.

These findings helped establish patterns to investigate during modeling.

### 3. Data Preparation

- Separated the features (`X`) from the target (`y`).
- Removed `customerID` from the modeling features.
- Split the data into 80% training data and 20% test data.
- Used stratified sampling to preserve the churn distribution across both sets.
- Applied one-hot encoding to categorical variables.

### 4. Logistic Regression

Trained Logistic Regression as a baseline model.

The baseline provided a reference point for evaluating more complex models. Hyperparameter tuning with cross-validation explored regularization strength and class weighting.

The class-weighted tuned model achieved:

| Metric | Test score |
|---|---:|
| Accuracy | 74.17% |
| Precision | 50.87% |
| Recall | 78.61% |
| F1-score | 61.76% |
| ROC-AUC | 0.8410 |

Class weighting improved recall compared with the original baseline, helping the model identify more actual churners at the cost of more false positives.

### 5. XGBoost

Trained an XGBoost classifier to capture potentially nonlinear relationships between customer characteristics and churn.

The initial model used:

- `n_estimators = 300`
- `max_depth = 4`
- `learning_rate = 0.05`
- `scale_pos_weight` calculated from the ratio of non-churners to churners in the training set.

The class weight was used to give greater importance to the minority churn class during training.

### 6. Model Evaluation

The initial XGBoost model achieved the following results on the test set:

| Metric | Test score |
|---|---:|
| Accuracy | 75.16% |
| Precision | 52.17% |
| Recall | 77.01% |
| F1-score | 62.20% |
| ROC-AUC | 0.8398 |
| PR-AUC (Average Precision) | 0.6574 |

The confusion matrix was:

| | Predicted stay | Predicted churn |
|---|---:|---:|
| Actual stay | 771 | 264 |
| Actual churn | 86 | 288 |

The model identified 288 of the 374 actual churners in the test set. However, it also incorrectly flagged 264 customers who stayed.

These results illustrate the trade-off between detecting more churners and generating false alarms.

### 7. Model Explainability with SHAP

Used SHAP (SHapley Additive exPlanations) to understand the features influencing XGBoost predictions.

The global summary plot highlighted these influential features:

1. Contract type — month-to-month
2. Tenure
3. Monthly charges
4. Online security — no
5. Total charges

A SHAP waterfall plot was also used to explain an individual customer's prediction by showing how feature contributions moved the model output away from its baseline.

SHAP describes how features contribute to the model's predictions; it does not establish causal relationships.

### 8. Business Impact: Customer Risk Ranking

Ranked test customers by their predicted probability of churn.

The top 10% of highest-risk customers contained:

- **Customers targeted:** 141
- **Actual churners within this group:** 109
- **Total actual churners in the test set:** 374
- **Share of actual churners captured:** 29.1%

This suggests that a risk-based ranking could help a retention team prioritize a limited number of customers for outreach.

However, the ranking also included customers who did not churn. The results should therefore be treated as exploratory estimates, not guaranteed retention outcomes.

## Technologies Used

- Python
- pandas
- NumPy
- scikit-learn
- XGBoost
- SHAP
- Matplotlib
- Jupyter Notebook / VS Code

## Project Structure

```text
customer-churn-prediction/
├── data/
│   ├── raw/
│   │   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│   └── processed/
│       └── telco_customer_churn_clean.csv
├── notebooks/
│   └── 01_data_collection_cleaning.ipynb
|   └── 02_EDA.ipynb
|   └── 03_Logistic_regression.ipynb
|   └── 04_xgboost.ipynb
├── README.md
└── requirements.txt
```

*Adjust the notebook filename and folder structure to match your actual project.*

## How to Run the Project

1. Clone or download the project repository.
2. Install the required Python libraries.
3. Place the original dataset in the expected data directory.
4. Open the notebook in Jupyter Notebook or VS Code.
5. Run the notebook cells in order to reproduce the analysis, train the models, evaluate performance, and generate SHAP explanations.

Install the main dependencies with:

```bash
pip install -r requirements.txt
```

## Conclusion

This project demonstrates an end-to-end customer churn prediction workflow, from data cleaning and exploratory analysis to model evaluation, explainability, and customer risk ranking.

Both Logistic Regression and XGBoost identified useful churn patterns. XGBoost achieved an F1-score of 62.20% and recall of 77.01% in the exploratory test evaluation. SHAP highlighted contract type, tenure, monthly charges, online security, and total charges as influential features.

The results illustrate how machine learning can help prioritize customer retention efforts while emphasizing the need for careful validation and business-aware decision-making.