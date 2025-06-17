#deep_learning

## One Line Summary
Similar to normalizing inputs to speed up learning, we normalize values of each neurons (usually before activations) in a layer $l$, so that the training parameters in $l+1$ will be faster. The "batch" in batch normalization reflects that we do the normalization for each mini-batch.

## Detail
### How to do batch normalization
Given inputs $x$ over a minibatch of size $m$ $B = \{x^{(1)}, ... x^{(m)}\}$, by applying transformation of your inputs using some learned parameters $\gamma$ and $\beta$, the outputs could be expressed as $B' = \{z^{(1)}, ... z^{(m)}\}$, where $z^{(i)}$ is the pre-activation corresponding to neuron $i$ in a layer.
	Normalization so that we have mean = 0 and variance = 1
	$$\mu = \frac{1}{m}\sum_{i = 1}^m z^{(i)}$$$$\sigma = \frac{1}{m}\sum_{i=1}^m(z^{(i)} - \mu)^2$$$$z^{(i)}_{norm} = \frac{z^{(i)} - \mu}{\sigma}$$
	Calculate new values for this layer, $\gamma$ and $\beta$ is learnable, so that the distribution of the values isn't limited to be mean = 0 and variance = 1 $$\tilde{z}^{(i)} = \gamma z^{i}_{norm} + \beta$$
### Incorporate batch normalization in training
for t = 1, ... mini_batches -> this is why it is called batch normalization
	compute forward propagation on $X^{\{t\}}$
		In each hidden layer, use batch normalization to replace $z^{[l]}$ with $\tilde{z}^{[l]}$
		Use back propagation to compute all gradients
		Use some optimizer to update the parameters
### Test time
- At test time we don't have mini-batches (e.g. only one test example) to calculate $\mu$ and $\sigma$
- Estimate $\mu$ and $\sigma$ with [[Exponentially Weighted Moving Averages]] over all the mini-batches during training
	- record all the $\mu$ and $\sigma$ for all the mini-batches for each layer
	- then use the equation of exponentially moving averages to calculate $\mu$ and $\sigma$ at test time
## Why does batch normalization work?
- Intuition 1: similar to normalizing inputs to speed up learning
- Intuition 2: reduce the amount that the distribution of hidden layer units shifts around (aka the mean and variance of the hidden layer units remain the same, i.e. internal covariate shift), so that the subsequent layer is easier to learn.
- Slight [[Regularization]] effect
	- Each mini-batch is scaled by the mean/variance computed on just that mini-batch
	- This adds some noise to the values of $z^{[l]}$ within that mini-batch. So similar to dropout, it adds some noise to each hidden layer's activations, and therefore has a slight regularization effect
### Reference
1. https://www.youtube.com/watch?v=nUUqwaxLnWs&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=29
2. https://www.youtube.com/watch?v=em6dfRxYkYU&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=28
3. https://www.youtube.com/watch?v=em6dfRxYkYU&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=27
4. https://www.youtube.com/watch?v=em6dfRxYkYU&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=30
5. https://www.youtube.com/watch?v=VIBQDCP3TZM

In batch normalization, input values of the same neuron for all the data in the minibatch are normalized. Widely used in feedforward network and CNNs
	Batch normalization is dependent on minibatch size, if the size is too small, it's not very stable.
	Batch normalization is not suitable for RNN because the input size varies.
In layer normalization, input values for all neurons in the same layer are normalized for each data sample. Widely used in NLP.
	layer normalization is less effective in CNNs
	LN can be slightly more computationally intensive in some cases since it normalizes over a larger set of parameters.


https://medium.com/biased-algorithms/batch-normalization-vs-layer-normalization-c44472883bf2