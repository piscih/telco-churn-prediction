### Logistic Regression — Initial Model Evaluation

The first Logistic Regression model achieved an accuracy of **80.55%** and a ROC-AUC score of **0.8421** on the test set.

The model achieved a precision of **65.72%**, a recall of **55.88%**, and an F1-score of **60.40%** for the churn class.

The confusion matrix showed that the model correctly identified 209 churners but missed 165 actual churners. This suggests that, although the model provides a useful baseline, its ability to identify customers at risk of leaving could be improved.

Accuracy alone is insufficient because the dataset contains more non-churning customers than churning customers. Therefore, recall, precision, F1-score, and ROC-AUC are also important evaluation metrics.

**Conclusion:** Logistic Regression provides a promising baseline model. Further experiments, including comparing other algorithms and tuning the classification threshold, may improve churn detection.