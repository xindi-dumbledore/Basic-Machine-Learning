#boosting #tree 

## High Level Summary
XGBoost, short for extreme gradient boost, is an optimized version of the [[Gradient Boosting Trees]], which is designed to be used with large and complicated dataset.

### Regression
- Make an initial prediction, 0.5 as default
- Build a XGBoost tree for the residuals (predict - true)
	- Starting putting all residuals in the root, then use different threshold to split the data in leaves
	- For each split, calculate similarity score for each leaf, $$\text{Similarity score} = \frac{(\sum_i\text{residual}_i)^2 }{\text{Number of residuals} + \lambda}$$, where $\lambda$ is the regularization parameter
	- Calculate $$\text{Gain} = \text{similarity(left)} + \text{similarity(right)} - \text{similarity(root)}$$
	- Keep building the tree until meeting some thresholds, e.g. depth, number of nodes in the leaf, etc.
- Pruning the tree based on gain values
	- Picking a number $\gamma$, calculate the difference between the gain associated with the lowest branch in the tree and $\gamma$: $$\text{Gain} - \gamma$$If it is positive, we are done pruning; if it is negative, we remove the branch and continue checking upper levels.
- Output Value for each leaf is $$\text{Output Value} = \frac{\sum_i\text{residual}_i }{\text{Number of residuals} + \lambda}$$
- New prediction is $$\text{Prediction} = \text{initial prediction} + \eta \times \text{Output Value}$$, where $\eta$ is the learning rate.
- Keep building trees on new obtained residual

### Classification
- The process of classification is very similar to the regression, with modification on how to calculate the similarity scores, output values and the final prediction
- Calculate similarity score for each leaf
$$Cover = \sum_i\text{previous probability}_i \times (1 - \text{previous probability})_i$$
$$\text{Similarity score} = \frac{(\sum_i\text{residual}_i)^2 }{\text{Cover} + \lambda}$$
- Calculate output value for each leaf
$$\text{Output Value} = \frac{\sum_i\text{residual}_i }{\text{Cover} + \lambda}$$
- Calculate prediction
$$\text{Prediction in odds} = \text{initial prediction in odds} + \eta \times \text{Output Value}$$
$$\text{Prediction in probability} = \frac{e^{\log(\text{prediction in odds})}}{1 + e^{\log(\text{prediction in odds})}}$$
### Connecting regression and classification
- The process of regression and classification can be unified with definition of loss functions $L(y_i, p_i)$
	- Regression $L(y_i, p_i) = \frac{1}{2}(y_i - p_i)^2$
	- Classification $L(y_i, p_i) = -[y_i \log p_i + (1-y_i) \log(1-p_i)] = -y_i \log(odds) + \log(1+e^{log(odds)})$
- The total loss function for each leaf with regularization can be written as $$[\sum_i^nL(y_i, p_i)] +\frac{1}{2}\lambda O_{value}^2$$, and the goal is to find an output value $O_{value}$ for the leaf that minimizes the above equation. 
- To obtain the optimal output value, we use 2nd order Taylor expansion to simplify the problem.
- Suppose our current prediction for $i$ is $p_i$, to build the next tree, the above equation can be written as 
$$
[\sum_i^nL(y_i, p_i+O_{value})] + \frac{1}{2}\lambda O_{value}^2 $$
Using Taylor expansion $$L(y_i, p_i+O_{value}) \approx L(y_i, p_i) + [\frac{d}{dp_i}L(y_i, p_i)]O_{value} + \frac{1}{2}[\frac{d^2}{dp_i^2}L(y, p_i)]O_{value}^2$$
Define $g_i = \frac{d}{dp_i}L(y_i, p_i)$ and $h_i = \frac{d^2}{dp_i^2}L(y, p_i)$, we can simplify the original equation 
$$\begin{align}
[\sum_i^nL(y_i, p_i+O_{value})] + \frac{1}{2}\lambda O_{value}^2 = \sum_i^n L(y_i, p_i)\\+ O_{value} \sum_i^n g_i \\ + \frac{1}{2}O_{value}^2 (\sum_i^n h_i + \lambda)
\end{align}$$
To obtain the optimal, we take the derivatives against $O_{value}$, and set to 0, we get
$$O_{value} = -\frac{\sum_i^n g_i}{\sum_i^n h_i + \lambda}$$
- Regression $$g_i = -(y_i - p_i)$$ $$h_i = 1$$
- Classification $$g_i = -(y_i - p_i)$$ $$h_i = p_i(1-p_i)$$
### Understanding $\lambda$ and $\gamma$
- when $\lambda > 0$, the values for similarity is smaller, and the gain is smaller, and it is easier to prune leaves, which prevents overfitting
- Setting $\gamma=0$ doesn't turn off pruning, because gain itself can be negative

## Optimizations to make XGBoost faster
### Approximate Greedy Algorithm
- Checking every single threshold for every single variable is expensive
- Divide the data into quantiles, and use quantiles as thresholds
### Parallel Learning
- Use parallel learning to split the dataset so that multiple computers can work on it
### Weighted Quantile Sketch
- The sketch algorithms will merges the data on different computers into an approximate histogram
- Weighted quantiles: sum of the weights in each quantiles are the same. 
- The weight for each observation is the 2nd derivative of the loss function, i.e. the Hessian
- The weight basically represents the confidence of the model for each observation
- Using weighted quantiles, we can get smaller quantiles when we need them, and focus on observations with low confidence
### Sparsity-aware Split Finding
- Dealing with missing values
- Split not missing values and missing values into separate tables. Build the tree using the data without missing values. When calculating gain, try the missing observations on both left and right to calculate gain_left and gain_right, and pick the one with the highest gain
### Cache-Aware Access
Put the gradients and hessians in the cache so we can rapidly calculate similarity scores and output values.
### Blocks for Out-of-Core Computation
Compress the data so that we don't need to read data from hard drive that much.
## Other Notes
- XGBoost can also add a L1 regularization together with the L2 regularization
## Reference
1. https://www.youtube.com/watch?v=OtD8wVaFm6E
2. https://www.youtube.com/watch?v=8b1JEDvenQU&t=0s
3. https://www.youtube.com/watch?v=oRrKeUCEbq8
4. https://albertum.medium.com/l1-l2-regularization-in-xgboost-regression-7b2db08a59e0