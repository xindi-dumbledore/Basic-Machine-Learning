
## Shapley Values

Shapley value is a concept in game theory to determine contribution of each player in a coalition or a cooperative game.

Assume
- $p$: number of members
- $v$: total value achieved through team work
- $\phi_m(v)$: fair share or payout to be given to each team member $m$

Then
$$\phi_m(v) = \frac{1}{p}\sum_s \frac{[v(S \cup \{m\}) - v(S)]}{ {p-1}\choose k(S)}, m = 1, 2, 3, ...,p$$
where $S$ is a sub-team without $m$, $k(S)$ is the size of $S$, and $S\cup \{m\}$ is the sub-team with $m$ joining.

**Essentially, we are calculating $m$'s added value (marginal contribution) when joining a sub-team.** 

### Shapely value in feature importance


For feature importance application, Each feature is a player and the payout is the model prediction.
Therefore, intuitively the process is, for each iteration:
- draw feature values in random  order for all features except for feature $j$
- calculate the difference of prediction with and without feature $j$
- take the average of difference from all combinations
#### Pros and Cons
Pros: Shapely value provides a fair contribution of features with mathematically proven theory and properties about its mechanism. It can be applied to almost all methods, especially to "black-box" models.
Cons: The complexity grows exponentially with the number of features

## SHAP: Shapely Additive exPlanations
SHAP is a method that combines Shapely values and LIME and provides more efficient solutions to calculate Shapely values.

### References
1. https://c3.ai/glossary/data-science/shapley-values/
2. https://towardsdatascience.com/using-shap-values-to-explain-how-your-machine-learning-model-works-732b3f40e137
3. https://proceedings.neurips.cc/paper_files/paper/2017/file/8a20a8621978632d76c43dfd28b67767-Paper.pdf
4. https://christophm.github.io/interpretable-ml-book/shap.html

