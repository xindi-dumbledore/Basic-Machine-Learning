#basic 

## Bias
Bias is the error introduced in the model due to oversimplification of the real world. High bias usually equals to underfitting.

## Variance
Variance is the error introduced in the model due to complex machine earning algorithm. When the model has high variance, the model learns random noise from the training dataset, leading to poor performance on test dataset, i.e. overfitting.

## Bias–variance Decomposition of MSE
Suppose on our data $x$, our true output values are $y$, and our model's prediction is $\hat{f}(x)$, and its expectation $E[\hat{f}(x)] \equiv \bar{f}(x)$.

Bias is $$\text{Bias} = E[\hat{f}(x) - y] = E(\hat{f}(x)) - E(y) = E[\hat{f}(x)] - y = \bar{f}(x) - y$$
Variance is $$\text{Variance} \\= E[(\hat{f}(x) - E[\hat{f}(x)])^2] 
= E[(\hat{f}(x) - \bar{f}(x)])^2]$$
MSE error is $$
\begin{aligned}
\text{MSE} = E[(y - \hat{f}(x))^2] \\= E[(y - \hat{f}(x) + \bar{f}(x) - \bar{f}(x))^2] \\= E[[(y - \bar{f}(x)) + (\bar{f}(x) - \hat{f}(x)]^2] \\ = E[(y - \bar{f}(x))^2] + E[\bar{f}(x) - \hat{f}(x))^2] \\+ 2E((y - \bar{f}(x))(\bar{f}(x) - \hat{f}(x))
\end{aligned}$$
$$\begin{aligned}
E((y - \bar{f}(x))(\bar{f}(x) - \hat{f}(x)) \\= (y - \bar{f}(x))E[\bar{f}(x) - \hat{f}(x)] = (y - \bar{f}(x))(E[\bar{f}(x)] - E[\hat{f}(x)]) = 0 \end{aligned}$$

Therefore $$\text{MSE} = E[(y - \bar{f}(x))^2] + E[\bar{f}(x) - \hat{f}(x))^2] = (y - \bar{f}(x))^2 + \text{variance} = \text{bias}^2 + \text{varaince}$$
## Bias-Variance Tradeoff
Ideally, we would like to achieve the sweet spot of low bias and low variance. When increasing the complexity of the model, we will see a reduction in error in bias. However, up to some point when our model is too complex, we see the increase of error due to variance. Therefore usually decreasing the bias will lead to increase in variance and vice versa. And this is called the bias-variance trade-off.

![[bias_variance.png]]

## Reference
1. https://www.cs.cornell.edu/courses/cs4780/2018fa/lectures/lecturenote12.html
2. https://en.wikipedia.org/wiki/Bias–variance_tradeoff#Bias–variance_decomposition_of_mean_squared_error
3. http://rasbt.github.io/mlxtend/user_guide/evaluate/bias_variance_decomp/
![[Bias_web.png]]![[Bias-Variance_Tradeoff_web.png]]