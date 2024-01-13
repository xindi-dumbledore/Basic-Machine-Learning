#NLP 
## One Line Summary
RNN is a family of neural networks that take sequential input of any length, apply the same weights on each step, and can optionally produce output on each step. RNNs are a great way to build a [[Language Modeling]]. Other more advanced RNN architectures include [[LSTM]] and [[GRU]]

## Simple/Vanilla/Elman RNN
- convert each word in the input sequence as a word embedding
- At each time step, calculate hidden states as the weighted sum of previous hidden state and input word embedding
- Key characteristic: the weight matrix on word embeddings and hidden states are shared
	![[simple_rnn.png]]
## Training RNN
- Get a big corpus of text, i.e. sequences of words
- Feed all the sequence into RNN, compute output distribution $\hat{y}^{(t)}$ for every time step $t$
- Not only the end of the sequence, but all the time steps in between
- Loss function on step $t$ is cross-entropy between predicted probability distribution $\hat{y}^{(t)}$ and the true next word $y^{(t)}$ (represented as a one-hot vector of word $x^{(t+1)}) $$J^{(t)}(\theta) = - \sum_{w\in V} y_w^{(t)}\log \hat{y}_w^{(t)} = - \log \hat{y}_{x_{t+1}}^{(t)}$$
- Overall loss is the average for the entire training set $$J(\theta) = \frac{1}{T}\sum_{t = 1}^T J^{(t)}(\theta)$$
- We use stochastic (actually mini-batch) gradient descent, updating the parameters on a batch of sentences for each mini-batch
## Backpropagations for RNN: **Backpropagation through time**
the gradient w.r.t. a repeated weight is the sum of the gradient w.r.t. each time it appears $$\frac{\partial J^{(t)}}{\partial W_h} = \sum_{i = 1}^t \frac{\partial J^{(t)}}{\partial W_h}|_{(i)}$$
## Pros and Cons
- Pros
	- Can process any length input
	- Computation for step t can use information from many steps back (in theory)
	- Model size doesn't increase for longer input context
	- Same weights applied on every time step, so there is symmetry in how inputs are processed
	- [[Vanishing and Exploding Gradients]]
- Cons
	- Recurrent computation is slow
	- In practice, difficult to access information from many steps back
## Bidirectional RNNs
We have a forward RNN, a backward RNN, and the hidden states are concatenated.
![[bidirectional_rnn.png]]
![[bidirectaional_rnn_eq.png]]
### Note
- Can only be used if we have access to entire input sequence
- Can't be used for language modeling
## Multi-layer RNN
- Send the hidden states to more layers of RNN. Stack the RNN layers.
- Usually not deep as convolutional or feed-forward networks
	- In machine translation, usually 2-4 layer for encoder RNN, 4 layer for decoder RNN
	- Even transformers just have 12 or 24 layers (with a lot of skip-like connections to help training)
![[multilayer_rnn.png]]