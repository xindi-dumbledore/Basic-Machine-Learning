For deep neural networks, it is very likely to encounter vanishing or exploding gradients. If the weights are a little bit higher than 1, we will have exploding gradients and if the weights are a little bit lower than 1, we will have vanishing gradients.

## Solution
- Better weight initialization
	- Initialize weights to small random values
	- Initialize hidden layers biases to 0, and output biases to optimal value if weights were 0 (i.e. mean of target value, or inverse sigmoid of mean of target value)
	- [[Xavier initialization]]
- Gradient clipping