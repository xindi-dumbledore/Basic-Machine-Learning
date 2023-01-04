#unsupervised #dimension-reduction

Principal component analysis is an unsupervised learning algorithm which can be used to reduce the dimension of your data. The model will collapses the data across the principal components. One can think of the first principal component (in a 2D dataset) as the line where there is the most amount of variance.

## Algorithm
1. Data preprocessing: normalization, or additional feature scaling, so that the data is centered (feature means are 0)
2. Two method to decompose:
	1. Method 1:
		1. Get covariance matrix $\Sigma=X^TX$ of feature matrix $X$
		2. Eigenvalue decomposition of the covariance matrix $\Sigma = VLV^T$, V is eigenvector matrix (each column is an eigenvector) and L is a diagonal matrix with eigenvalues.
	2. Method 2:
		1. Perform [[Singular Value Decomposition (SVD)]] on the feature matrix $\text{SVD}(X) = USV^T$, where $U$ is the eigenvectors, $S$ is the eigenvalues
3. To obtain new data, we first determine the number of columns $n$ we want to retain, then the new data can be obtained through $XU[:, 0:n]$
4. The variance retained can be calculated as $\sum_i^nS_{ii}^2$, and one can set a threshold (e.g. 95% of the variance) to choose appropriate $n$ 
## Kernel PCA #todo 

![[Principal_Component_Analysis_web.png]]![[Kernel_PCA_web.png]]![[Selecting_Number_Of_Components_In_PCA_web.png]]