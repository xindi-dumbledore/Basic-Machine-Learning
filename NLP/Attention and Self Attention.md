## One line summary
Attention treats each word's representation as a query to access and incorporate information from a set of values.

Attention operates on queries $q_i$, keys $k_i$ and values $v_i$. The calculation includes three steps:
- Compute key-query similarities
- Compute attention weights from similarities (softmax)
- Compute outputs as weighted sum of value

## Why attention
In traditional [[Seq2Seq]] model, the last hidden state of the encoder is viewed as the encoding of the source sentence. This requires it to capture all information about the source sentence. Information bottleneck!

By introducing attention, we enable direct connection to the encoder on a particular part of the source sequence.

## Seq2Seq with Attention
- Encoder hidden states $h_1, ..., h_N$ (keys and values)
- On time step t, we have decoder hidden state $s_t$ (query)
- Attention scores $$e^t = [s_t^Th_1, ..., s_t^Th_N]$$
- Take softmax to get attention distribution $$\alpha_t = \text{softmax}(e^t)$$
- Attention output: weighted sum of the encoder hidden states $$a_t = \sum_{i=1}^N \alpha_i^th_i$$
- Concatenate attention output with decoder hidden state, and use this to predict the word $$[a_t;s_t]$$
![[attention.png]]
## Self Attention in detail
Self attention basically means attention within a single sentence. Therefore in self-attention, query, key and value are drawn from the same source.
- For example, if the output of the previous layer is $x_1, ... x_T$, we could let $v_i = k_i = q_i = x_i$, then the calculation is: $$e_{ij} = q_i^Tk_j, \alpha_{ij} = \frac{\exp(e_{ij})}{\sum_{j'}\exp(e_{ij'})}, a_i = \sum_j \alpha_{ij}v_j$$
### Masking the Future in Self Attention
- To use self-attention in decoders, we need to ensure we can't peek at the future: when $j >= i$, $$e_{ij} = -\infty$$
## Multihead Attention

## Reference
1. https://web.stanford.edu/class/archive/cs/cs224n/cs224n.1214/slides/cs224n-2021-lecture07-nmt.pdf