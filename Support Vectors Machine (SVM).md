#basic #classification 
### High Level Summary
Support Vectors Machine (SVC) is a supervised algorithm that aims to find a hyperplane in an N-dimensional space(N — the number of features) that distinctly classifies the data points.

Our objective is to find a plane that has the maximum margin, i.e the maximum distance between data points of both classes. Maximizing the margin distance provides some reinforcement so that future data points can be classified with more confidence.

## Details
### Notation
We use $y_i = 1$ and $y_i = -1$ to denote the two classes.

### Large Margin Classifier
SVM tries to fit the widest possible hyperplane (decision boundary)  to separate the classes. The decision boundary is fully determined (or supported) by the most extreme instances of the class, and these instances are called support vectors (circled back in the below figure)
![[SVM diagram.png]]

### Why not maximum margin classifier?
A natural idea is that we find the decision boundary that generates the maximum margin possible. However, this is **very sensitive to outliers.** Imagine one instance of class A is very close to class B. Using maximum margin classifier, we will get a decision boundary very close to class B because of that outlier.
![[maximum margin classifier problem.png]]

### Soft Margin Classifier
To deal with the problem of maximum margin classifier, we want to build a soft margin classifier, which accept some misclassifications in order to better generalize the margins. We focuses on two objectives:
- Maximize the distance between the decision boundary and support vectors (maximum margin, i.e. hard SVM) $$\max \frac{1}{||w||} = \min \frac{1}{2}||w||^2 \ s.t. \ y_i(w^Tx_i - b) \geq 1$$
- Minimize the cost a data point violates the margin, using a slack variable $$ \sum_i^m \epsilon_i$$
	- $\epsilon$ values
		- if $\epsilon = 0$, the observation is correctly classified
		- if $0 < \epsilon < 1$, the observation is inside the margins
		- if $\epsilon \geq 1$, the observation is misclassified
	- One common option is the Hinge Loss $$\sum_{j=1}^m \max(0, 1 - t_j y_j)$$, where $t_j = w^T x_j + b$, which penalize misclassifications and also classifications close to the boundary (not confident).
- Combination loss function (with hinge loss) $$\min [C\sum_{j=1}^m max(0, 1-t_jy_j) + \frac{1}{2}||w||^2] \ s.t. \ y_i(wx_i - b) \geq 1$$
	- Large C, lower bias, high variance
	- Small C, higher bias, low variance
### Kernel Trick
The above discussion is on linearly separable dataset, but that is usually not the case. On these dataset, we want to transform the data into high-dimensional space (by adding more features such as polynomials), where it will become linearly separable. Directly mapping is very costly, but luckily we have the kernel trick to the rescue.

The "trick" in kernel trick is that we don't explicitly apply the transformation, rather we use pairwise similarities (i.e. inner product) to achieve the effect. 

In other words, kernel function defines the inner product of two data points in the new space.

### Process
- Given a kernel function $K(x, x')$ 
- For training example $x^{(i)}$, we compute a set of new features $$f^{(i)} = [K_1^{(i)}, K_2^{(i)}, ... K_m^{(i)}]^T$$, where $K_j^{(i)} = K(x^{(i)}, x^{(j)})$
- We treat $f^{(i)}$ as the new features for data point $x^{(i)}$, and apply the algorithm on  $f^{(i)}$.

### Common kernels
- Polynomial kernel $$K(x, x') = (1 + x^Tx')^p$$ which map the data to $n^d$ dimensions
- Gaussian/Radial kernels (polynomials of all orders) $$K(x, x') = \exp(-\frac{||u - v||^2}{2\sigma^2})$$which map the data to infinite dimension

### What is support vector?
The observations on the edge and within the soft margin are called support vectors.

## References
1. https://towardsdatascience.com/machine-learning-algorithms-from-start-to-finish-in-python-svm-d9ff9b48fd1
2. Jure Leskovec: https://www.youtube.com/watch?v=8xbnLHn4jjQ
3. https://stats.stackexchange.com/questions/74499/what-is-the-loss-function-of-hard-margin-svm
4. https://programmathically.com/what-is-a-support-vector/
5. https://illustrated-machine-learning.github.io/pages/machine-learning/linear-algorithms.html#support-vector-machines