#LTR 

## High Level Summary
LambdaRank is a pairwise [[Ranking Models]] built on [[RankNet]]. LambdaRank defined the gradient directly (without defining its corresponding loss function) by taking ranking loss into consideration: scale the RankeNet's gradients by the size of the change in NDCG if document $i$ is swapped with $j$.

## Detail
$$ \frac{\partial C^{LambdaRank}_{ij}}{\partial W_k} = \frac{\partial C^{RankNet}_{ij}}{\partial W_k}|\Delta\text{NDCG}_{ij}|$$
where $|\Delta\text{NDCG}_{ij}|$ is the change in NDCG ([[Learning to Rank Evaluation Measures#Normalized DCG (NDCG)]]) if document $i$ is swapped with $j$.

## Reference
1. https://louiskitlunglaw.medium.com/ranknet-lambdarank-tensorflow-implementation-part-iv-3ac4e77ee2c5