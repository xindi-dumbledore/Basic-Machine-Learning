#evaluate 
This page listed common regression evaluation measures. They can be used for models like [[Linear Regression]], [[Decision Tree]] Regressor, etc.

## Notation
$n$: number of observations
$d$: number of features
$y_i$: actual value of observation $i$
$\hat{y_i}$: predicted value of observation $i$

## Mean Square Error
$$MSE = \frac{1}{n} \sum_i^n (y_i - \hat{y_i})^2$$
- The most intuitive evaluation metric. Some close variations:
	- Mean Absolute Error: where we substitute the square to absolute.
	- Root Mean Square Error: where we take a squared root of MSE. 
- This is a widely used loss function for regression task. Closely related to Maximum Likelihood Estimation (MLE).
- Need to compare with other MSE numbers to understand whether a model is good or bad
- The range is $[0, \inf)$, can only be useful compare different models on the same dataset, but not comparing across datasets

## $R^2$ and Adjusted $R^2$
$R^2$ looks at how much variance in the target vector is explained by the features, i.e. explained variation/total variation. The Adjusted $R^2$ takes into account the number of feature being used (penalize on models with more but not useful features).
$$R^2 = 1 - \frac{RSS}{TSS} = 1- \frac{\sum_i^n(y_i - \hat{y_i})^2}{\sum_i^n(y_i - \bar{y})^2}$$
where RSS is the abbreviation for Residual Sum of Squares, and TSS is Total Sum of Squares. 
- Pros
	- The range is $[0,1]$, and directly tell whether the model is good (1) or bad (0)
- Cons:
	- Can't determine whether the coefficient estimation is biased #todo 
	- Adding a feature will ALWAYS increase the score
	- $R^2$ is biased and tends to be higher

To handle the second point of con, adjusted $R^2$ is introduced to penalize on models with more but not useful features:
$$\text{Adjusted }R^2 = 1 - \frac{RSS/(n-d-1)}{TSS/(n-1)}$$

## Others
### Mallow's $C_p$
Mallows’ $C_p$ is used when we have several potential predictor variables that we’d like to use in a regression model and we’d like to identify the best model that uses a subset of these predictor variables. 

We can identify the “best” regression model by identifying the model with the lowest $C_p$ value that is less than P+1, where P is the number of predictor variables in the model.

$$C_p = \frac{RSS_p}{s^2} - N + 2(p+1)$$
$p$ is the number of features selected, and $s^2$ is estimation of $\sigma^2$.

### AIC ([[Akaike information criteria]])
Similar to Mallow's $C_p$, AIC is used to compare which model is better in situations like feature selection.
$$AIC = -2 (\text{log likelihood}) + 2d$$
### Explained Sum of Square (ESS)
$$ESS = \sum_i^n(\hat{y_i} - \bar{y})^2$$
This is the exact thing of "variance" in [[Bias and Variance Tradeoff]] formula. Which measure the amount of variance in the model.

## Reference
1. https://www.statisticshowto.com/akaikes-information-criterion/
2. https://www.statisticshowto.com/mallows-cp/
3. https://www.statisticshowto.com/probability-and-statistics/statistics-definitions/adjusted-r2/