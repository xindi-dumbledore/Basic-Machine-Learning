#tree 
## Training procedure
- Find the feature (or split criteria for continuous variable) that generate the best split of the data
	- Impurity functions: evaluate "best" split
		- achieve a maximum at the uniform distribution
		- achieve a minimum when $p_i=1$
		- be symmetric with regard to their permutations.
	- Classification
		- gini impurity
			- gini impurity = 1 - gini = $1 - \sum_i^k p_i^2$ = $\sum_i^k p_i(1 - p_i)$
		- information gain
			- information gain = 1 - entropy = $1 - \text{Weighted}( -\sum_i^k p_i\log p_i)$
	- Regression: mean squared error
		- For each split, calculate impurity of each leaf, then calculate weighted average of the impurity (weighted by number of datapoints)
		- For numerical feature, test each possible threshold
	- For each impure leaf node, repeat the split process for the subset of the dataset
## Prediction
- Classification: take the majority class of a leaf node
- Regression: take the average number of the leaf node
# Pruning: to avoid overfit
- Pre-pruning
	- Maximum depth: The tree has reached the maximum depth threshold
	- Minimum samples per leaf: Ignore leaf with less than threshold sample
- Post-pruning: build a overfit tree to classify training set perfectly first then prune
	- Cost complexity Pruning (Weakest Link Pruning)
		- Define error rate of a tree $T$ over data $S$ as $R(T, S)$
		- At each step, we remove the subtree $t$ that minimizes $\frac{R(T - t, S) - R(T, S)}{|T| - |T-t|}$
		- Build all the subtree till there is only 1 node in the tree
		- Select optimal subtree: use cross-validation technique to select the best subtree
		- Equivalent understanding
			-  For a tree $T$, given $\alpha$ as the complexity parameter, we calculate the cost-complexity measure $R_\alpha(T) = R(T) + \alpha |T|$, where $R(T)$ is the performance score of the tree $T$ (e.g. sum of residuals for regression tasks, misclassification rate for classification task) and $|T|$ is the number of leaf nodes in $T$. The cost-complexity measure is a tradeoff between performance and tree complexity.
			- For each step, we select the smallest possible $\alpha$ that $R_\alpha(T-t) < R_\alpha(T)$
## Pros and Cons
- Pros
	- Interpretability
	- Can handle both categorical and numerical data
- Cons
	- Prone to overfit -> Pruning
	- Can be unstable to small variations of the data
	- **Greedy algorithm** cannot guarantee global optimal
	- Can create biased trees if some classes dominate

## Reference
- https://www.youtube.com/watch?v=_L39rN6gz7Y
- https://www.youtube.com/watch?v=g9c66TUylZ4
- https://www.youtube.com/watch?v=D0efHEJsfHo
- https://online.stat.psu.edu/stat508/lesson/11/11.8/11.8.2
- https://www.youtube.com/watch?v=KF-4ci6RTA4
- https://en.wikipedia.org/wiki/Decision_tree_pruning#Cost_complexity_pruning
![[Decision_Trees_web.png]]
![[Decision_Tree_Regression_web.png]]![[Gini_Index_web.png]]