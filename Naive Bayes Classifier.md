#basic #classification 

- Assumption: each feature makes an independent and equal contribution to the outcome -> why it is naive
- Given features $(x_1, ..., x_n)$, and label $y$, using Bayes theorem:
$$P(y|x_1, ..., x_n) = \frac{P(x_1, ...x_n|y)P(y)}{P(x_1, ...x_n)}$$
Using the assumption that each feature is independent:

$$\frac{P(x_1, ...x_n|y)P(y)}{P(x_1, ...x_n)} = \frac{P(x_1|y)P(x_2|y)...P(x_n|y)P(y)}{P(x_1)P(x_2)...P(x_n)}$$

Because the denominator is constant, we ignore it, therefore:
$$P(y|x_1, ..., x_n) \propto P(x_1|y)P(x_2|y)...P(x_n|y)P(y) = P(y)\prod_i^nP(x_i|y)$$
- If the feature is categorical, we simply count to get $P(x_i|y)$, if it is numerical, we can assume some distribution over the features (e.g. Gaussian), and calculate probability using that
- Inference
	- We simple compute $P(y|x1, ...,x_n)$ for each possible $y$, normalize the obtained probabilities, and pick the one with the highest probability.
![[Gaussian_Naive_Bayes_Classifier_web 1.png]]
## Reference
1. https://www.geeksforgeeks.org/naive-bayes-classifiers/