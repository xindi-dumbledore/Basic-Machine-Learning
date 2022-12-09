#boosting #tree

## Gradient Boosting
Gradient Boosting is a generic framework that can be applied on any loss function that is differentiable.

The "gradient" in gradient boosting can be viewed as this:
- in traditional machine learning, we have a explicit form of loss function, and we calculate gradient on the parameters in the loss function
- in gradient boosting, we don't have explicit form of loss function, therefore, we calculate the gradient of the loss function respect to the predicted value
## Gradient Boosting General Framework
- Input: Data $\{(x_i, y_i\}_{i=1}^n$, and a differentiable loss function $L(y_i, F(x))$
- Step 1: Initialize model with a constant value: $F_0(x) = argmin_{\gamma} \sum_{i=1}^n L(y_i, \gamma)$
- Step 2: For m = 1 to M (i.e. build M trees):
	- Compute pseudo residual $$r_{im} = -[\frac{\partial L(y_i, F(x_i))}{\partial F(x_i)}]_{F(x) = F_{m-1}(x)}$$ for $i = 1, ..., n$
	- Fit a weak learner on the pseudo residual  $r_{im}$  and create terminal regions (i.e. leaves) $R_{jm}$, for $j = 1 ... J_m$ 
	- Calculate output values for each leaf: For $j = 1 ...J_m$ (i.e. each leaf), $\gamma_{jm} = argmin_{\gamma} \sum_{x_i\in R_{jm}}^n L(y_i, F_{(m-1)}(x_i) + \gamma)$,
	- Update the prediction function, where $\nu$ is the learning rate: $F_m(x) = F_{m-1}(x) + \nu \sum_{j =1}^{J_m} \gamma_{jm} I(x\in R_{jm})$

## Gradient Boosting for Regression
- $L(y_i, F(x)) = \frac{1}{2}(y_i - F(x))^2$, i.e. in the same fashion of MSE
- $F_0(x) = \frac{1}{n}\sum_i^n y_i$, i.e. the mean of $y_i$
- $r_{im} = -[y_i - F(x_i)]_{F(x) = F_{m-1}(x)}$, i.e. residual calculated with last step prediction
- Fit a regression tree to the $r_{im}$ values and create terminal regions (i.e. leaves) $R_{jm}$, for $j = 1 ... J_m$ 
- Calculate output values for each leaf: For $j = 1 ...J_m$ (i.e. each leaf), $\gamma_{jm} = argmin_{\gamma} \sum_{x_i\in R_{jm}}^n L(y_i, F_{(m-1)}(x_i) + \gamma) = \frac{1}{|R_{jm}|}\sum_{x_i \in R_{jm}}y_i$, i.e. average value of each leaf
- $F_m(x) = F_{m-1}(x) + \nu \sum_{j =1}^{J_m} \gamma_{jm} I(x\in R_{jm})$, i.e. update the prediction function by adding all the output values for each leaf, and multiply by the learning rate $\nu$

## Gradient Boosting for Classification
- $L(y_i, F(x)) = y_i \log (p) + (1-y_i) \log(1-p) = -y_i \log(odds) + \log(1+e^{log(odds))}$, i.e. in the same fashion of logistic regression loss function (i.e. binary cross entropy)
- $F_0(x) = \log(odds) = \log(p/1-p)$, i.e. the mean of $y_i$
- $r_{im} = -[y_i - p]_{F(x) = F_{m-1}(x)}$, i.e. residual calculated with last step prediction
- Fit a regression tree to the $r_{im}$ values and create terminal regions (i.e. leaves) $R_{jm}$, for $j = 1 ... J_m$ 
- Calculate output values for each leaf: For $j = 1 ...J_m$ (i.e. each leaf), $\gamma_{jm} = argmin_{\gamma} \sum_{x_i\in R_{jm}}^n L(y_i, F_{(m-1)}(x_i) + \gamma)$
	- Approximate the Loss function using 2nd order Taylor Polynomial Expansion, then take the derivative on the Taylor expansion
	- $\gamma = \sum_i \frac{\sum {residual}}{\sum {p(1-p)}}$
- $F_m(x) = F_{m-1}(x) + \nu \sum_{j =1}^{J_m} \gamma_{jm} I(x\in R_{jm})$, i.e. update the prediction function by adding all the output values for each leaf, and multiply by the learning rate $\nu$

## Reference
https://www.youtube.com/watch?v=3CC4N4z3GJc
https://stats.stackexchange.com/questions/338658/gradient-in-gradient-boosting