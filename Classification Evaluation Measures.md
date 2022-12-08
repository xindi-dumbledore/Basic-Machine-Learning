#evaluate

## Confusion Matrix
Confusion matrix is the table contains 4 outputs from binary classifier. Various measures can be calculated from the confusion matrix.
![[confusion_matrix.png]]
## Basic measure from confusion matrix
Denote $P$ and $N$ as total number of actual positives and negatives:
1. Accuracy: $$\frac{TP+TN}{P+N}$$
It is biased when the class is imbalance
2. Error Rate: $$\frac{FP+FN}{P+N}$$
3. Precision: what percentage of predicted positives are actual positives $$\frac{TP}{TP+FP}$$
4. Recall (Sensitivity, True Positive Rate): what percentage of actual positives are predicted as positives $$\frac{TP}{P} = \frac{TP}{TP + FN}$$
5. Specificity (True Negative Rate) $$\frac{TN}{N}$$
6. False Positive Rate: what percentage of actual negatives are predicted as positives $$\frac{FP}{N}$$
### Combination of Basic Measures
1. F1 Score: Harmonic mean of precision and recall, range from 0 (bad) to 1(good) $$2\times \frac{Precision * Recall}{Precision + Recall}$$
2. Youden's J index: range from 0(bad) to 1(good) $$Sensitivity + Specificity - 1$$
3. ROC (Receiver Operating Characteristic) and AUC (Area Under the Curve)
ROC plots True Positive Rate against False Positive Rate at every probability threshold (decision threshold) of a binary classifier. The best ROC curve is closer to the top left corner. AUC is the area under the ROC curve, ranges from 0 (completely wrong) to 0.5 (random classifier) to 1 (perfect classifier).
![[Receiver_Operating_Characteristic_web.png]]
## Relationship with Type I error and Type II error
In hypothesis testing:
- Type I error: null hypothesis is true, but we reject it
- Type II error: null hypothesis is false, but we didn't reject it
Follow the convention of treating null hypothesis as 0, and alternative hypothesis as 1:
- Type I error is False Positive  (actual 0, predict 1), therefore related to precision and false positive rate
- Type II error is False Negative (actual 1, predict 0), therefore related to recall
## Multi-class classification measurement
1. We can calculate above basic metrics for each class (one vs rest), and aggregate them (e.g.take the mean). FOR ROC curve, we can also generate a curve for each class.
2. Cohen's kappa coefficient #todo
3. Matthew's correlation coefficient #todo

## References
1. Multi-class evaluation: https://towardsdatascience.com/comprehensive-guide-on-multiclass-classification-metrics-af94cfb83fbd