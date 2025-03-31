#LTR 

## High Level Summary
RankNet is a pairwise learning to rank model.

## Detail
### Model Target
RankNet model the target probabilities between any 2 documents ($d_i$ and $d_j$) of the same query. The target probabilities of $d_i$ and $d_j$ is defined as follows where $s_i$ is the relevant score of $d_i$:
- $P_{ij} = 1$, if $s_i > s_j$
-  $P_{ij} = 0.5$, if $s_i = s_j$
-  $P_{ij} = -1$, if $s_i < s_j$

The cost function for RankNet aims to minimize the number of inversions in ranking. Here an inversion means an incorrect order among a pair of results, i.e. when we rank a lower rated result above a higher rated result in a ranked list.

### Model Structure
$x_i$ and $x_j$ as feature vectors for $d_i$ and $d_j$. We pass the $x_i$ and $x_j$ to the same neural network to get two outputs $o_i$ and $o_j$. $\hat{P}_{ij}$ is then calculated by applying sigmoid on $o_i - o_j$. Then the loss is the cross entropy loss ([[Common Loss Function Glossary#Cross Entropy]]) between $\hat{P}_{ij}$ and $P_{ij}$.

![[ranknet.png]]
### Training Details
- Cost function $$\begin{aligned}C_{ij} = -P_{ij}\log\hat{P}_{ij} - (1-P_{ij})\log(1 - \hat{P}_{ij}) \\= -P_{ij}[\log \hat{P}_{ij} + \log (1 - \hat{P}_{ij})] - \log(1 - P_{ij}) \\= -P_{ij} o_{ij} + \log(1 + e^{o_{ij}})\end{aligned}$$
- Gradients $$\frac{\partial C_{ij}}{\partial W_k} = \frac{\partial C_{ij}}{\partial o_{ij}} \frac{\partial o_{ij}}{\partial W_k} = \frac{\partial C_{ij}}{\partial o_{ij}} (\frac{\partial o_{i}}{\partial W_k} - \frac{\partial o_{j}}{\partial W_k})$$ $$\frac{\partial C_{ij}}{\partial o_{ij}} = -P_{ij} + \frac{e^{o_{ij}}}{1 + e^{o_{ij}}} = -P_{ij} + \hat{P_{ij}}$$
### Inference time
At inference time, after obtaining the features $x_i$, we obtain the output value $o_i$ passing $x_i$ into the trained neural network, then we can use $o_i$ to rank the items.
## Reference
1. https://medium.com/swlh/ranknet-factorised-ranknet-lambdarank-explained-implementation-via-tensorflow-2-0-part-i-1e71d8923132