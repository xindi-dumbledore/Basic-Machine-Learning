#NLP 
## High level summary
The Transformer Encoder-Decoder 

## Issues with RNN
- Linear interaction distance
	- nearby words often affect each other's meanings, but it needs much longer steps for distant word pairs to interact
- Lack of parallelizability
	- Because it is rolled from left to right, future RNN hidden states is dependent on past RNN hidden states, so we cannot run things in parallel
## How Transformer get rid of Recurrent
- Self Attention (see [[Attention and Self Attention#Self Attention in detail]])
- Problem of self-attention alone:
	- Self attention will lose sequence order!: Position representation
		- Method 1: Sinusoidal position representations
		- Method 2: learn position representation from scratch
	- No nonlinearities for deep learning! (it's just weighted averages): Add a feed-forward network to pos-process each output vector
	- Need to ensure we don't "look at future" when predicting a sequence! : [[Attention and Self Attention#Self Attention in detail#Masking the Future in Self Attention]]
## Details
![[Pasted image 20221215095641.png]]
![[Pasted image 20221215095650.png]]
### Key-Query-Value Attention
In transformer, we don't simply set key, query and value to all be the input embeddings. Rather, we have learnable matrices: key matrix, query matrix and value matrix to obtain the key, query and value.
$$k_i = Kx_i, q_i = Qx_i, v_i = Vx_i$$
#### Matrix Representation
Let $X = [x_1;...;x_T] \in R^{T\times d}$ be the concatenation of input vectors.
- Query x Key is $XQ(XK)^T = XQK^TX^T$
- Take softmax $\text{softmax}(XQK^TX^T)$
- Calculate values $\text{softmax}(XQK^TX^T)XV$
### Multi-headed Attention
With multi-headed attention, we can look at the sentences "multiple times", each time putting emphasis on different places.
- For each "head", we have a different $Q_h, V_h, K_h$ matrix
- We calculate the attention for each head separately
- Finally, the attention from all heads are concatenated $[a_1, a_2, ...a_h]$
### Encoder-Decoder Cross-Attention

### Tricks to help with training
- Residual connections
- [[Layer Normalization]]
- Scaling the dot product in attention
	- After calculate Query x Key, divided by $\sqrt{d/h}$
		- $\text{softmax}(\frac{XQK^TX^T}{\sqrt{d/h}})XV$