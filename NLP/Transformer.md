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
	- No nonlinearities for deep learning! (it's just weighted averages): Add a feed-forward network to post-process each output vector
	- Need to ensure we don't "look at future" when predicting a sequence! : [[Attention and Self Attention#Self Attention in detail#Masking the Future in Self Attention]]
## Details
![[transformer_encoder.png]]
![[transformer_decoder.png]]
### Key-Query-Value Attention
In transformer, we don't simply set key, query and value to all be the input embeddings. Rather, we have learnable matrices: key matrix, query matrix and value matrix to obtain the key, query and value.
$$k_i = Kx_i, q_i = Qx_i, v_i = Vx_i$$
#### Matrix Representation
Let $X = [x_1;...;x_T] \in R^{T\times d}$ be the concatenation of input vectors, where $T$ is the number of tokens and $d$ is the embedding size
- Query x Key is $XQ(XK)^T = XQK^TX^T$
- Take softmax $\text{softmax}(XQK^TX^T)$
- Calculate values $\text{softmax}(XQK^TX^T)XV$
### Multi-headed Attention
With multi-headed attention, we can look at the sentences "multiple times", each time putting emphasis on different places.
- For each "head", we have a different $Q_h, V_h, K_h$ matrix
- We calculate the attention for each head separately
- Finally, the attention from all heads are concatenated $[a_1, a_2, ...a_h]$
### Encoder-Decoder Cross-Attention
We also attend decoder to encoder.
- Query: vectors from decoder $Z = [z_1; ...;z_T]$, $Q$ as query matrix
- Key and value: output vectors from the encoder $H = [h_1;...;h_T]$, $K$ and $V$ as key and value matrix
- dot product: $(ZQ)(HK)^T$
- softmax: $\text{softmax}(ZQK^TH^T)$
- attention value: $\text{softmax}(ZQK^TH^T)(HV)$
### Tricks to help with training
- Residual connections
- [[Layer Normalization]]
- Scaling the dot product in attention
	- After calculate Query x Key, divided by $\sqrt{d/h}$
		- $\text{softmax}(\frac{XQK^TX^T}{\sqrt{d/h}})XV$