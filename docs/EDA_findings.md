### Numerical Features by Churn — Findings

**1. Tenure:** Customers who churned had a median tenure of approximately 10 months, compared with 38 months for customers who stayed. This suggests that churn is associated with shorter customer relationships. An unusually high-tenure observation was also identified among churners.

**2. MonthlyCharges:** Customers who churned had a higher median monthly charge (approximately 80) than customers who stayed (approximately 65). Monthly charges may be associated with churn, although contract types and service choices may also contribute to this pattern.

**3. TotalCharges:** Customers who churned had lower median total charges (approximately 500) than customers who stayed (approximately 1,800). This may partly reflect shorter tenure. Several potential outliers were observed among churners and should be investigated rather than automatically removed.

**Overall conclusion:** Tenure, monthly charges, and total charges show differences between customers who stayed and those who left. These features may be useful for churn prediction, but their predictive value must be evaluated during model development.


### Churn Analysis by Contract Type

The analysis shows that month-to-month contracts have the highest churn rate at **42.71%**, followed by one-year contracts at **11.27%** and two-year contracts at **2.83%**.

This suggests that customers with shorter-term contracts are more likely to leave the company, while customers with longer-term contracts tend to remain. Contract type may therefore be an important feature for predicting customer churn. However, this relationship does not establish causation.


### Churn Analysis by Internet Service

The churn rate is highest among fiber optic customers at **41.89%**, followed by DSL customers at **18.96%**. Customers without internet service have the lowest churn rate at **7.40%**.

Internet service type may be an important feature for predicting churn. The higher churn rate among fiber optic customers warrants further investigation, but the observed relationship does not establish the underlying cause.

### Churn Analysis by Payment Method

Electronic check customers have the highest churn rate at **45.29%**. In comparison, the churn rates for mailed checks, automatic bank transfers, and automatic credit card payments are **19.11%**, **16.71%**, and **15.24%**, respectively.

Customers using automatic payment methods show lower churn rates than those using electronic checks. Payment method may therefore be a useful feature for predicting customer churn. Further analysis is needed to determine whether this relationship is influenced by other variables, such as contract type or tenure.

### Churn Analysis by Paperless Billing

Customers using paperless billing have a churn rate of **33.57%**, compared with **16.33%** among customers who do not use paperless billing. This indicates an association between paperless billing and higher customer churn.

Paperless billing may be a useful feature for predicting churn. However, the observed relationship does not establish causation, and other customer characteristics may contribute to this difference.

### Churn Analysis by Online Security

Customers without online security have a churn rate of **41.77%**, compared with **14.61%** for customers who have online security. Customers without internet service have a churn rate of **7.40%**.

The results suggest that online security subscription status is associated with customer churn. Customers without online security are more likely to leave, making this feature potentially useful for churn prediction. However, the relationship does not establish causation, and other factors may contribute to the observed differences.

### Churn Analysis by Technical Support

Customers without technical support have a churn rate of **41.64%**, compared with **15.17%** among customers with technical support. Customers without internet service have a churn rate of **7.40%**.

This suggests that technical support subscription status is associated with customer churn. Customers without technical support are more likely to leave, making this feature potentially useful for churn prediction. However, this association does not establish causation.


### Churn Analysis by Online Backup

Customers without online backup have a churn rate of **39.93%**, compared with **21.53%** among customers who subscribe to online backup. Customers without internet service have a churn rate of **7.40%**.

The results suggest that online backup subscription status is associated with customer churn. Customers without online backup are more likely to leave, making this feature potentially useful for predicting churn. However, the observed relationship does not establish causation.

### Churn Analysis by Device Protection

Customers without device protection have a churn rate of **39.13%**, compared with **22.50%** among customers who subscribe to device protection. Customers without internet service have a churn rate of **7.40%**.

The results suggest that device protection subscription status is associated with customer churn. Customers without device protection are more likely to leave, making this feature potentially useful for churn prediction. However, the observed relationship does not establish causation.

### Churn Analysis by Multiple Lines

Customers with multiple phone lines have a churn rate of **28.61%**, compared with **25.04%** for customers without multiple lines and **24.93%** for customers without phone service.

The differences between these groups are relatively small compared with those observed for contract type and several internet-related services. Therefore, `MultipleLines` appears to have a weaker standalone association with churn, although it may still contribute to a predictive model when combined with other features.

### Churn Analysis by Senior Citizen Status

Senior citizens have a churn rate of **41.68%**, compared with **23.61%** for non-senior citizens. This represents a difference of approximately 18 percentage points.

The results suggest that senior citizen status is associated with customer churn and may be useful for prediction. Further analysis is needed to understand how this relationship interacts with other customer characteristics.


### Churn Analysis by Partner and Dependents

Customers without a partner have a churn rate of **32.96%**, compared with **19.66%** for customers with a partner. Similarly, customers without dependents have a churn rate of **31.28%**, compared with **15.45%** for customers with dependents.

These results suggest that partner and dependent status are associated with customer churn. Customers without a partner or dependents show higher churn rates in this dataset. These relationships may help inform churn prediction, although they do not establish causation.

### Churn Analysis: Gender, Phone Service, and Streaming Services

Gender has very similar churn rates for female customers (26.92%) and male customers (26.16%). Phone service also shows a relatively small difference, with churn rates of 26.71% for customers with phone service and 24.93% for those without it.

For StreamingTV, the churn rate is 33.52% among customers without the service and 30.07% among customers with it. For StreamingMovies, the corresponding rates are 33.68% and 29.94%. Customers without internet service have a churn rate of 7.40% in both streaming comparisons.

Overall, gender and phone service show relatively small differences in churn rates, while the streaming features show somewhat larger differences. These are exploratory associations and do not establish causation.

### Correlation Analysis

The correlation analysis shows a strong positive relationship between `tenure` and `TotalCharges` (0.83), suggesting that customers who remain longer generally accumulate higher total charges. `MonthlyCharges` and `TotalCharges` also show a moderate-to-strong positive relationship (0.65). In contrast, `tenure` and `MonthlyCharges` have a weak positive correlation (0.25).

The numerical features will be retained for the initial modeling stage. The relationship between tenure and total charges will be considered when interpreting model results.