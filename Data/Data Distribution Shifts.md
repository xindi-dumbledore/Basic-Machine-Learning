#designing-ml-systems #data
p.g. 237 of *[[Designing Machine Learning Systems]]*

Data distribution shift refers to the phenomenon in supervised learning when the data a model works with changes over time, which causes this model’s predictions to become less accurate as time passes.

## Type of Data Distribution Shifts

We view the training data as a set of samples from the joint distribution $P(X, Y)$, then ML usually models $P(Y|X)$. The joint distribution $P(X,Y)$ can be decomposed in two ways:
- $P(X, Y) = P(Y|X)P(X)$
- $P(X, Y) = P(X|Y)P(Y)$

$P(Y|X)$ - conditional probability of an output given an input
$P(X)$ - probability density of the input
$P(Y)$ probability density of the output

### Covariate shift
- $P(X)$ changes but $P(Y|X)$ remains the same
- Example: breast cancer detection
	- risk of breast cancer is higher for women over the age of 40
	- have more women over the age of 40 in the training data than in the inference data
	- $P(X)$: probability for a sample with age higher than 40, changed
	- $P(Y|X)$: risk of breast cancer agains age, unchanged
- Potential reasons
	- Biases during data selection process, e.g. we get data from a breast cancer test center, people over 40 are encouraged to do more checkups
	- Training data is artificially altered to make it easier for the model to learn
	- Active learning, where we use samples most helpful in the training
	- Major change of environment
### Label shift
- $P(Y)$ changes but $P(X|Y)$ remains the same
- Example: breast cancer detection
	- there are more women over 40 in the training data, so the percentage of POSITIVE labels is higher than in the inference data, $P(Y)$ is different
	- If randomly select person A with breast cancer from the training data, and person B with breast cancer from test data, A and B have the same probability of being over 40, $P(X|Y)$ is the same
### Concept shift
- $P(Y|X)$ changes but $P(X)$ remains the same
- Same input, different output
- Example:
	- Before COVID-19, a 3-bedroom apartment in SF cost $2 million.
	- After COVID-19, people are moving out of SF, so the market cools down, and the same apartment cost $1.5 million
	- Because it's same apartment $P(X)$ is the same, but $P(Y|X)$ changes

## Detecting Data Distribution Shifts
- Monitor model performance
	- Data distribution shifts are only a problem if they cause your model’s performance to degrade. 
	- So the first idea might be to monitor your model’s accuracy-related metrics—accuracy, F1 score, recall, AUC-ROC, etc.—in production to see whether they have changed.
	- To monitor, we need ground-truth labels
- Monitor input distribution
	- Basic statistics of two distributions (mean, max, median, quantiles, etc.)
	- Two-sample hypothesis test to compare distributions
		- e.g. KS test
		- caveat: statistical significant different doesn't mean it's important
- Time scale windows for detecting shifts
	- Treat input data to ML applications as time-series data
	- Do time-series analysis

## Addressing Data Distribution Shifts
- Train on massive datasets, with the hope that if the training data is large enough, data encounter in production will likely come from the training distribution
- Adapt a trained model to a target distribution without requiring new labels
- Retrain the model using the labeled data from target distribution (more widely used in production)