#information-retrieval

The usage of ranking models is mostly in **sorting documents by relevance to find contents of interest with respect to a query.**

The problem can then be abstracted as given each input $x=(q,d)$, where $q$ is a query and $d$ is a document, we want to predict a relevance score $s=f(x)$. Then we can rank the documents according to those scores.
![[ranking_model_abstraction.png]]

There are two types of scoring models in general:
- [[Vector space models]] (i.e. Neural Vector Search). Compute a embedding vector (e.g. using [[TF-IDF]] or [[BERT]]) for each query and document, and then compute the relevance score $f(x) = f(q, d)$ as the similarity (e.g. cosine similarity) between the embeddings of $q$ and $d$.
- Learning to Rank. We learn a machine learning model to predict a score given an input $x = (q,d)$ during training phase where some ranking loss is minimized.

## Learning to Rank
### Input and Output
- Input: for each query $q$ we have $n$ documents $D = {d_1, ..., d_n}$ to be ranked by relevance. The elements $x_i = (q, d_i)$ are the inputs to our model.
- Output: for a query-document input $x_i = (q, d_i)$, we assume there exists a true relevance score $y_i$. Our model outputs a predicted score $s_i = f(x_i)$.
### Approaches (& Loss Functions)
- Pointwise method
	- How closely is the $s_i$ to $y_i$?
	- The problem is transformed into a regression problem.
	- Limitation: we need true relevance score for each document, which is sometimes not available
	- Example: Subset Ranking and MSE loss
- Pairwise method
	- For each pair of element $x_i = (q, d_i)$ and $x_j = (q, d_j)$, if $y_i > y_j$, does $s_i > s_j$? i.e. relative preference
	- The problem is transformed into a binary classification problem
	- Example
		- [[RankNet]], Binary Cross Entropy Loss (still need some relevancy score for each document)
		- [[LambdaRank]], directly obtain gradients of an implicit loss function. Documents with high rank would have bigger gradients.
		- [[LambdaMART]], gradient boosted LambdaRank
- Listwise method
	- Take the whole list of element, we want the predicted ranking and actual ranking as close as possible
	- The most direct approach: we are directly maximizing some ranking evaluation metric ([[Learning to Rank Evaluation Measures]])
	- Challenge: we need to sort based on the scores to calculate those evaluation metric, and sorting is not differentiable (i.e. no gradients)
		- [[SoftRank]]
			- predict a smoothened probabilistic score $s \sim N(f(x), \sigma^2)$. Then we can compute probability distributions for the ranks of each document. SoftNDCG which is a smooth function over NDCG is the loss function
		- [[ListNet]]
			consider each ranked list corresponds to a permutation, and define a loss over space of permutations.
		- [[LambdaLoss]]
			- A mixture model where the ranked list $\pi$ is treated as a hidden variable. Loss is defined as the negative log likelihood.
			- Generalized framework for all other listwise methods

## Reference
1. https://towardsdatascience.com/learning-to-rank-a-complete-guide-to-ranking-using-machine-learning-4c9688d370d4
2. https://embracingtherandom.com/machine-learning/tensorflow/ranking/deep-learning/learning-to-rank-part-2/#converting-scores-and-relevance-labels-into-probability-distributions