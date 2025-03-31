#basic #classification

- Hypothesis$$h(x^{(i)}, \theta) = \text{sigmoid}(\theta ^T x^{(i)})$$where $\text{sigmoid}(x) = \frac{1}{1 + \exp (-x)}$
- Prediction (in real practice, we can use other threshold than 0.5)
$$\hat{y^{(i)}} = h(x^{(i)}, \theta) \geq 0.5$$
![[logistic regression hypothesis.png]]
- Loss function
$$J(\theta) = -\frac{1}{m} \sum_{i=1}^m[y^{(i)}\log h(x^{(i)}, \theta) + (1-y^{(i)})\log (1-h(x^{(i)}, \theta))]$$
- Derivation of the loss function (MLE)
![[logistic regression lost function.png]]
- Interpretation of logistic regression
	- Odds Ratio
	- 
## References
1. https://www.coursera.org/learn/classification-vector-spaces-in-nlp/supplement/b3fHH/optional-logistic-regression-cost-function