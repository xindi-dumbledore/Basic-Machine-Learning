#tree #bagging 
### High Level Summary
Random forest is an extended bagging method which combines the output of multiple decision trees to make a prediction. The key difference between it with traditional bagging is that it uses feature randomness to create an uncorrelated forest of decision trees.

## Detail
- Each tree is trained on bootstrap sample: a data sample drawn from the training set with replacement.
- During the training of each tree, at each candidate split, only a random subset of the features are used. Typically if the total number of features is $p$, $\sqrt{p}$ features are used in each split.
	- **we end up with trees that are not only trained on different sets of data (thanks to bagging) but also use different features to make decisions.**
- To make prediction, we can take the majority votes (classification) or average (regression) on the prediction of each tree
![[Random_Forest_web.png]]![[The_Random_In_Random_Forest_web.png]]
## References
1. https://towardsdatascience.com/understanding-random-forest-58381e0602d2
2. https://en.wikipedia.org/wiki/Random_forest#Preliminaries:_decision_tree_learning
3. https://www.ibm.com/cloud/learn/random-forest