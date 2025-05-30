#tree #boosting 

- AdaBoost = Adaptive Boosting
- Training Procedure
	- Assign every observation $x_i$ an initial weight value $w_i = \frac{1}{n}$ where n is the total number of observations
	- Train a weak model (most often a [[Decision Tree]] with only 1 split, i.e. decision stump)
	- For each observation
		- Calculate **Total Error** $\text{TE} = \frac{w_i \times \text{number of wrongly predicted}}{n}$
		- Calculate **Importance** (or confidence, or amount of say) of this classifier $\alpha = \frac{1}{2}\ln\frac{1 - \text{TE}}{\text{TE}}$
			- $0 \leq \alpha \leq 1$, 0 indicates perfect model and 1 indicates horrible model
		- If predicted incorrectly, increase $w_i = w_i \times e^{\alpha}$
		- If predicted correctly, decrease $w_i = w_i \times e^{-\alpha}$
		- Normalize the weights so that they sum up to 1
	- Train a new weak model using resampled data of the same size, where the updated $w_i$ is the sampled weight
		- Alternative: use weighted gini index for the new weak model
	- Repeat step 3 and 4 until observations are perfectly predicted or a preset number of trees are trained.
- Prediction
	- For a test example $z_i$, obtain its prediction by all the weak learners $(c_1, c_2, ..., c_j)$, and get the class with majority (sum amount of say together)
- Pros and Cons
	- Pros
		- Less prone to overfitting as the input parameters are not jointly optimized
		- improved accuracy
		- interpretability
	- Cons: needs a quality dataset - noisy data and outliers have to be avoided
- Questions
	- Can it apply to regression problem?
		- Yes! Modify the Total Error equation to reflect average regression loss (one can use linear, square or exponential loss, need to make sure $L_i \in [0, 1]$. Average is weighted average.), and calculate $\alpha = \frac{TE}{1-TE}$. Update the weights as $w_i = w_i \alpha^{(1-L_i)}$

## Reference
	- https://www.analyticsvidhya.com/blog/2021/09/adaboost-algorithm-a-complete-guide-for-beginners/
	- https://www.researchgate.net/publication/2424244_Improving_Regressors_Using_Boosting_Techniques
	- https://www.youtube.com/watch?v=LsK-xG1cLYA
![[AdaBoost_web.png]]