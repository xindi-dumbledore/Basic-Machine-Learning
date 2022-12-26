#LTR 
## High Level Summary
ListNet is a listwise learning to rank algorithm.

## Detail
### Permutation Probability
Permutation probability is the likelihood of a permutation (ranking list of given items) given the ranking function.

The assumption is that given a list of items, any permutations (i.e. ranking) is possible, but different permutations have different likelihood calculated based on the ranking function (something we would like to model)

Given $n$ items, we define a single permutation as $\pi = <\pi(1), \pi(2), ..., \pi(n)>$, where $\pi(j)$ denotes the object at position $j$ in this permutation. All possible permutations of the $n$ items constitutes $\Omega_n$.

Suppose we have a real number (can be considered as relevance score) for each item, then we can obtain a list of scores for the permutation $\pi$, as $s = (s_1, s_2, ..., s_n)$, where $s_j$ is the score of $\pi(j)$. Then we can calculate the permutation probability as $$P_s(\pi) = \prod_{j = 1}^n \frac{\phi(s_j)}{\sum_{k=j}^n \phi(s_j)}$$
In the paper, $\phi(.) \equiv e^x$.

**Characteristics of this permutation probability**
- If we sort the items in descending order with the scores, we achieve the highest permutation probability
- If we sort the items in ascending order with the scores, we achieve the lowest permutation probability

**Issues of permutation probability**
Calculating permutation probability is expensive. There are $n!$ permutations given $n$ items.

### Top One Probability
Top one probability for a given item $j$ can be calculated as the sum of the permutations where item $j$ is ranked first: $$P_s(j) = \sum_{\pi(1) = j, \pi \in \Omega_n}P_s(\pi)$$
It is found that we can calculated the Top One Probability without calculating permutation probability $$P_s(j) = \frac{\phi(s_j)}{\sum_{k=1}^n\phi(s_k)} = \frac{\exp(s_j)}{\sum_{k=1}^n\exp(s_k)}$$, which is exactly a softmax function over the relevance scores. **Now we can convert the relevance scores into probability distributions, and we can compare it with the ground truth.** The paper uses Cross Entropy as the loss function.

### Obtaining scores
For each (query $q$, document $j$) pair, we use a feature vector to represent this pair (e.g. embeddings). Then we send this feature vector to a neural network to learn the score of the document $j$. Then for each $q$, we can calculate the loss function using the top-1 probability and the ground-truth distribution.
![[listNet data.png]]

## Reference
1. https://www.microsoft.com/en-us/research/wp-content/uploads/2016/02/tr-2007-40.pdf
2. https://embracingtherandom.com/machine-learning/tensorflow/ranking/deep-learning/learning-to-rank-part-2/#converting-scores-and-relevance-labels-into-probability-distributions