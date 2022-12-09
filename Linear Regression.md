#regression #basic

- Multicollinearity
	- What: when independent variables in a regression model are correlated

- Random notes
	- Using one-hot encoding for categorical features in linear regression would increase the sparsity (i.e. curse of dimensionality) problem, and would lead overfitting
	- Beware of dummy variable trap: because one-hot encoding creates a value for each category, it will create perfect multicollinearity. Drop one of the value in the dummy variables to prevent it.
	- We can use Lasso regression to regularize the model and prevent some problems.

https://towardsdatascience.com/one-hot-encoding-multicollinearity-and-the-dummy-variable-trap-b5840be3c41a