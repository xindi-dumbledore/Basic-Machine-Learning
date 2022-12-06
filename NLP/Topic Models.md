#NLP 
Topic models offer a way to get a corpus-level view of major themes. They are unsupervised models.

## Matrix Factorization Approach
Given document x terms matrix, we can use matrix factorization to convert them into document x topic matrix and topic x terms matrix. If the factorization method is SVD, this technique is called latent semantic analysis (LSA).
![[LSA.png]]

## Generative Model - Latent Dirichlet Allocation
The idea of a generative model is that we want to "simulate" the process how a document is wrote, i.e. how each word in the document is generated. The process is as follows:
1. Get the topic-word "dice": what words are used in each topic with what probability
2. Get the document-topic "dice": what topics are covered in this document with what probability
3. For each word, we first determine its topic using the document-topic "dice", then we determine the specific word using topic-word "dice"

To describe it in a more mathy way:
- For each topic $k \in \{1, ... K\}$, draw a multinomial distribution $\beta_k$ from a Dirichlet distribution with parameter $\lambda$ (topic-word dice)
- For each document $d \in \{1, ..., M\}$, draw a multinomial distribution $\theta_d$ from a Dirichlet distribution with parameter $\alpha$ (document-topic dice)
- For each word position $n \in \{1, ..., N\}$, select a hidden topic $z_n$ from the multinomial distribution parametrized by $\theta$
- Choose the observed word $w_n$ from distribution $\beta_{z_n}$

### Where is Dirichlet?
- Dirichlet分布是由Beta分布衍⽣来的， Dirichlet分布是多项分布的参数p的先验分布。 在⼀个多项分布中， 每⼀项的概率pi 如何确定？ 在Bayesian学派认为， 多项分布的参数p应该是服从⼀个概率分布的， 可以认为服从Dirichlet分 布， 也就是说Dirichlet分布是多项分布的参数的分布， 被认为是“分布上的分布”。
- 在LDA模型中， 每篇⽂档的topic分布服从⼀个多项分布， 同时这个topic分布（多项分布）的参数又服从⼀个Dirichlet分布。 每⼀篇⽂档的都对应⼀个不同的topic分布， 即多项分布。 同时， LDA中的每个topic下存在⼀个term的单词多项分布， 即每个topic下的单词都服从多项分布， 并且每个topic对应的多项分布的参数都服从⼀个Dirichlet分布， 这也是为什么LDA的名字由来， 因为存在两个隐含的Dirichlet分布。

### Inference: Gibbs Sampling