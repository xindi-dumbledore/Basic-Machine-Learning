For deep neural networks, it is very likely to encounter vanishing or exploding gradients. If the weights are a little bit higher than 1, we will have exploding gradients and if the weights are a little bit lower than 1, we will have vanishing gradients.

## Vanishing and Exploding Gradients in RNN
The problem of vanishing and exploding gradients is more prominently in RNN as the weights are shared across time steps, so we have repeated multiplication by the same weight matrix

**Vanishing gradients**
Gradient signal from far away is lost because it's much smaller than gradient signal from close-by. So model weights are updated only with respect to near effects, not long-term effects. Therefore, it is hard for the model to learn dependency between words

**Exploding gradients**
- If the gradient becomes too big, the SGD update step becomes too big and it's hard to do optimization
- Can cause number overflow


## Solution
- Better weight initialization
	- Initialize weights to small random values
	- Initialize hidden layers biases to 0, and output biases to optimal value if weights were 0 (i.e. mean of target value, or inverse sigmoid of mean of target value)
	- [[Xavier initialization]]
- Gradient clipping (for exploding gradient)
	- if gradient $g$ is higher than a given threshold, we update the gradient to be $$g = \frac{threshold}{||g||}g$$
	- so that we take a step in the same direction, but a smaller step
- Having memory (for vanishing gradients in RNN)
	- We have vanishing gradients problem because the hidden state is constantly being rewritten with the new input, so that we lose history
	- Manually add memory in the architecture to preserve information over many steps: [[LSTM]]
- Add more direct connections from lower layer to higher layer output (for vanishing gradients in general architecture)
	- ResNet: introducing residual connections, also known as skip-connections
	- DenseNet: directly connect each layer to all future layers