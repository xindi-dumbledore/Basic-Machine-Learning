#regression #basic

### Main Idea
- Use least-squares to fit a line to the data
- Calculate $R^2$
- Calculate a p-value for $R^2$ 

### Assumptions
- Linear relationship
	- There exists a linear relationship between the coefficient of the parameters (independent variables) and the dependent variable Y.
- Residuals (i.e. errors) are normally distributed
	- From central limit theorem: total error is a sum of error for each Y_i, and central limit theorem says if there are a large number of i.i.d. random variables, then the distribution of their sum tends to be a normal distribution.
	- The assumption of the residuals are normally distributed leads to the estimators (i.e. coefficients) are also normally distributed. This allows us to use t and F tests for hypothesis testing on the estimators.
- Homoscedasticity
	- Variance of residuals is constant across all values of the independent variable X
	- Example of heteroscedasticity (i.e. not homoscedasticity): savings vs income data
		- As incomes grow, people have more discretionary income and thus a wider choice about the income disposition. Thus, regressing savings on income is likely to find higher variance as income increases cause people have more choices regarding their saving decision.
	- If the data is not homoscedastic, observation with higher variance will have a larger influence when doing estimation, thus the OLS estimation of the coefficient will not have minimum variance.
	- We can transform the variable Y using log or sqrt to mitigate this problem
- No Multi-Collinearity
	- No (low) correlation between independent variables.
	- **Beta gives the rate of change in the response variable y as X1 changes by one unit, keeping all other Xs constant.** When there is a high correlation between say independent variables X1 and X2, it is not possible to keep X2 constant as it will change with the change in X1. **For data with multicollinearity, Betas will thus take multiple values, and there is no unique solution for the regressor coefficients. Therefore, in case of high multicollinearity, the beta estimates are indeterminate and the standard errors are infinite.**
- No autocorrelation between errors
	- The error term of one observation shouldn't be influenced by the error term of another observation
	- Usually a problem with time series data. Usually, observations at adjacent time intervals will have correlated errors.
	- Influence on OLS: The estimated standard errors tend to underestimate the true standard error. P value thus associated is lower. This leads to conclusion that a variable is significant even when it is not. The confidence and prediction intervals are narrower than what they should be.

### Verify the assumptions
- Linear relationship
	- Use residual plot. 
		- `residuals = y_test - y_pred`
		- `residual plot: plt.scatter(y_pred, residuals)``
	- The residual plot should not show any pattern i.e. the residuals should be randomly dispersed around the horizontal axis.
- Residuals are normally distributed
	- P - P (probability-probability) plot
		- P-P plot assess how closely a theoretical distribution models a given data distribution
		- x-axis: theoretical percentiles of the normal distribution
		- y-axis: sample percentiles of the residuals
		- ideally it will be a 45 degree diagonal line
	- Anderson Darling Test #todo 
		- Measures how well the data follows a particular distribution. The smaller the better fit
- Homoscedasticity
	- Residual plots. Heteroscedasticity produces a distinctive fan or cone shape in residual plots.
	- Breusch Pagan Test #todo
- Multi Collinearity
	- Scatter plot between independent variables
	- Variance inflation factor (VIF)
		- Calculated by taking a predictor and regressing it against every other predictor in the model (i.e. we predict the $X_i$ using all other features in $X$), after doing that, we obtain an $R^2$
		- $\text{VIF} = \frac{1}{1-R^2}$, The larger the VIF, the more correlated the variable is with other regressors. Usually higher than 3 is considered bad
- Autocorrelation
	- Durbin Watson test #todo 

## Find coefficients
- Least Square Method (OLS)
	- Minimize mean square error
		- estimation
		- hypothesis testing
	- OLS estimation provides the Best Linear Unbiased Estimate (BLUE) of beta if all assumptions of the linear regression are satisfied.
- MLE (Maximum likelihood estimation)
	- The likelihood is $P(Y|X,b,a,\sigma^2) = \prod_{i=1}^n p(y_i|x_i,b,a,\sigma^2)$
	- $p(y_i|x_i,b,a,\sigma^2) = \frac{1}{\sqrt{2\pi\sigma^2}}\exp{\frac{-(y-(b+ax))^2}{2\sigma^2}}$
- Machine Learning
	- Cost function: Mean Square Error
	- Algorithm: Gradient Descent

## Other Random notes
- Using one-hot encoding for categorical features in linear regression would increase the sparsity (i.e. curse of dimensionality) problem, and would lead overfitting
- Beware of dummy variable trap: because one-hot encoding creates a value for each category, it will create perfect multicollinearity. Drop one of the value in the dummy variables to prevent it.
- We can use Lasso regression to regularize the model and prevent some problems.

## References
1. https://towardsdatascience.com/one-hot-encoding-multicollinearity-and-the-dummy-variable-trap-b5840be3c41a
2. https://towardsdatascience.com/linear-regression-assumptions-why-is-it-important-af28438a44a1