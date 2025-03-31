Ensemble learning is a learning technique in which multiple individual models are combined to create a meta model.

## Examples
- [[Boosting]]
- [[Bagging]]
- [[Stacking]]
## Differences between Bagging and Boosting
- bagging is a **parallel** learning process and boosting is a **sequential** learning process

![[bagging vs boosting.png]]
## Why Ensemble Works
- Imagine you have three email spam classifiers, each with an accuracy of 70%. Assuming that each classifier has an equal probability of making a correct prediction for each email, and that **these three classifiers are not correlated.**
- For each email, each classifier has a 70% chance of being correct. The ensemble will be correct if at least two classifiers are correct.
![[why ensemble works.png]]
- This ensemble will have an accuracy of 0.343 + 0.441 = 0.784, or 78.4%.
### Uncorrelated of base models
- If all classifiers are perfectly correlated—all three of them make the same prediction for every email—the ensemble will have the same accuracy as each individual classifier. 
- **When creating an ensemble, the less correlation there is among base learners, the better the ensemble will be.**
- It’s common to choose very different types of models for an ensemble. For example, you might create an ensemble that consists of one transformer model, one recurrent neural network, and one gradient-boosted tree.
## Pros and Cons of Ensemble Models
- Pros
	- Generally have higher performance
	- Prevents overfitting
		- With a _bagging_ approach, each model should be tuned to overfit. Model independence is exploited because bagging is a variance reduction technique. Predictions can be softened for improved stability. These models are run in parallel and averaged. 
		- With _boosting_, models are used sequentially and wrong classifications from prior runs are given more weight. Boosting is a bias reduction technique. 
		- Stacking can be done with random forests. Stacking improves accuracy while keeping variance _and_ bias low.
- Cons
	- Can be more difficult to interpret
	- Ensembles cost more to create, train and deploy