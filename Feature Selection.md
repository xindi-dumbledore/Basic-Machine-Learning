#basic 
![[feature selection techniques.png]]
**Feature selection** is the process of reducing the number of input variables when developing a predictive model.

It is desirable to reduce the number of input variables to both reduce the computational cost of modeling and, in some cases, to improve the performance of the model.

## Supervised vs Unsupervised
- Supervised: use the target variable
- Unsupervised: don't use the target variable

## Wrapper vs Filter
- Wrapper: Create many models with different subsets of input features and select those features that result in the best performing model according to a performance metric. Example [RFE](https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFE.html)
- Filter: Use statistical techniques to evaluate the relationship between each input variable and the target variable, and these scores are used as the basis to choose (filter) those input variables that will be used in the model.

## Intrinsic Feature Selection
Some machine learning algorithms that perform feature selection automatically as part of learning the model, for example:
- Lasso
- Decision tree
- Random forest

## Filter-based Feature Selection
Most of these techniques are univariate, meaning that they evaluate each predictor in isolation.
![[Pasted image 20230103170529.png]]

After obtaining the statistics, we can choose the top k features with the best statistics.

## Wrapper-based Feature Selection
- Forward selection
	- Starts with one predictor and adds more iteratively. At each subsequent iteration, the best of the remaining original predictors are added based on performance criteria.
- Backward Elimination
	- Starts with all predictors and eliminates one-by-one iteratively. One of the most popular algorithms is Recursive Feature Elimination (RFE) which eliminates less important predictors based on feature importance ranking.
- Bi-directional elimination (Stepwise Selection)
	- Bi-directional, based on a combination of forward selection and backward elimination. It is considered less greedy than the previous two procedures since it does reconsider adding predictors back into the model that has been removed (and vice versa).
## Feature Importance
- Feature Importance refers to techniques that calculate a score for all the input features for a given model — the scores simply represent the “importance” of each feature. A higher score means that the specific feature will have a larger effect on the model that is being used to predict a certain variable.
- Some common feature importance
	- Gini impurity: used in [[Decision Tree]]
	- Permutation feature importance (also called Mean Decrease Accuracy)
		- The feature importance is calculated by noticing the increase or decrease in error when we permute the values of a feature.
- We can use feature importance score to do feature selection
## Other notes
- Relationship between feature selection and dimensionality reduction
	- Dimensionality Reduction also reduces fewer input variables, but unlike feature selection, dimensionality reduction will transform the input data. Therefore it is an alternative to feature selection
## References
https://machinelearningmastery.com/feature-selection-with-real-and-categorical-data/
https://towardsdatascience.com/feature-selection-for-machine-learning-in-python-wrapper-methods-2b5e27d2db31
https://towardsdatascience.com/understanding-feature-importance-and-how-to-implement-it-in-python-ff0287b20285
https://towardsdatascience.com/a-relook-on-random-forest-and-feature-importance-2467dfab5cca