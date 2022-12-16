#deep_learning 
## One line Summary
Input values in all neurons in the same layer are normalized for each data sample. In other word, it treats each output as a data sample with features, and normalize across the features. 



## Detail
### [[Batch Normalization]] Cons
- hard to use sequence data
- hard to use with small batch sizes
- hard to parallelize
- training time and testing time is different
And Layer Normalization solves each one of them!

### Definition
Given inputs $x$ over a minibatch of size m, $B=\{x_1,x_2,…,x_m\}$, each sample $x_i$ contains $K$ elements, i.e. the length of flatten $x_i$ is $K$

$$\mu_i=\frac{1}{k}\sum_{k=1}^K x_{i,k}$$
$$\sigma^2 = \frac{1}{K}\sum_{k=1}^K(x_{i,k} - \mu_i)^2$$
$$x_{i,k}^{norm} = \frac{x_{i,k} - \mu_i}{\sigma}$$

$$\tilde{x}_i=\gamma x_i^{norm}+\beta$$

We can see from the math above that **layer normalization has nothing to do with other samples in the batch.**

LayerNorm's success may be due to its normalizing gradients

## Usages
[[Recurrent Neural Networks (RNN)]]
[[Transformer]]

![[batch_norm.png]]
![[layer_norm.png]]
## References
1. https://www.pinecone.io/learn/batch-layer-normalization/
2. https://leimao.github.io/blog/Layer-Normalization/

