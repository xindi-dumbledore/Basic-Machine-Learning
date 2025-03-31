#LTR #evaluate 

## Precision@k
Proportion of recommended items in the top-k set that are relevant

``Precision@k = (# of recommended items @k that are relevant) / (# of recommended items @k)``

## Recall@k
Proportion of relevant items found in the top-k recommendations

``Recall@k = (# of recommended items @k that are relevant) / (total # of relevant items)``

Limitation: Precision@k and Recall@k only takes 0/1 judgement, also it doesn't take into account the ranking positions (so swap some ranking results might lead to same score)

## Average Precision(AP)
AP is the sum of precision@k for different values of k divided by the total number of relevant items in the top k results. AP penalize models that are not able to rank relevant items high in the list.
$$AP = \frac{1}{\text{total \# of relevant items}} \sum_{k=1}^n \text{Precision@k } \times \text{Relevance@k}$$
``
## Mean Average Precision (MAP)
Mean Average Precision (MAP) is simply AP over all queries.

## Mean Reciprocal Rank (MRR)
Average of the reciprocal ranks of "the first relevant item" over a set of queries Q

$$MRR = \frac{1}{|Q|}\sum_{i = 1}^{|Q|}\frac{1}{\text{rank}_i}$$
Limitation: It only takes the top relevant item into account, not suitable for case for a list of related items.

## Normalized Discounted Cumulative Gain (NDCG)
Normalized Discounted Cumulative Gain (NDCG) takes the order and relative importance of the documents into account, and values putting highly relevant documents high up the recommended list.

### Discounted Cumulative Gain (DCG)
$$DCG_{@k} = \sum_{i = 1}^k \frac{G_i}{\log_2(i+1)}$$
where $G_i$ is the predicted relevancy score of document at rank $i$.

### Ideal Discounted Cumulative Gain (IDCG)
It's the same formula as DCG, just switching predicted relevancy score/ranking to actual relevancy score/ranking

$$IDCG_{@k} = \sum_{i = 1}^{k_{\text{ideal}}} \frac{G_i^{k_{\text{ideal}}}}{\log_2(i+1)}$$
### Normalized DCG (NDCG)
$$NDCG_{@k} = \frac{DCG_{@k}}{IDCG_{@k}}$$


Advantage: takes into account actual relevancy score (rather than 0/1 judgement) and ranking positions
Limitation: doesn't penalize for bad documents in the result.

## Spearman Rank Correlation
Measure the strength and direction of association between two ranked variables. It basically tells how well the relationship between two variables could be represented using a monotonic function.

$$\rho = 1 - \frac{6 \sum d_i^2}{n(n^2 - 1)}$$
where $d_i$ is the rank difference between two list of the same item $i$, and $n$ is the total number of items. The higher the number, the higher the correlation.

## Kendall's Tau Rank Correlation
Kendall's Tau is very similar to Spearman Rank Correlation, but is demonstrated to be more robust to errors. The calculation relies on number of concordant (C) and discordant (D) pairs. See [here](https://www.statology.org/kendalls-tau/) for a detailed calculation example.

$$\tau = \frac{C-D}{C+D}$$

## Reference
1. https://medium.com/@m_n_malaeb/recall-and-precision-at-k-for-recommender-systems-618483226c54
2. https://machinelearninginterview.com/topics/machine-learning/ndcg-evaluation-metric-for-recommender-systems/
3. https://www.simplilearn.com/tutorials/statistics-tutorial/spearmans-rank-correlation
4. https://www.statology.org/kendalls-tau/
5. https://towardsdatascience.com/breaking-down-mean-average-precision-map-ae462f623a52
6. https://web.stanford.edu/class/cs276/handouts/EvaluationNew-handout-1-per.pdf