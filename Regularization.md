#basic #overfitting
## L-2 regularization
add $\frac{\lambda}{2m} ||w||_2 ^ 2 = \frac{\lambda}{2m}\sum_{i=1}^n w_n^2$ to the loss function (Frobenius norm for neural network, i.e.)
- alternative name: weight decay
- if linear model, it's called Ridge Regression

## L-1 regularization
- add $\frac{\lambda}{2m} ||w||_1 ^ 2 = \frac{\lambda}{2m}\sum_{i=1}^n|w_n|$ to the loss function
- If linear model, it's called Lasso Regression
- $w$ will be sparse, in a sense doing feature selection
- L-1 regularization gives a sparse solution (weights will be dragged to 0)
	- why?
		- The L1-norm form a sparky "diamond" shape on the parameters. We enlarge this diamond to touch the decision boundary, and the sparky end are more likely to touch the decision boundary first, leading to sparse solution
		- Details check this [blog_post](https://blog.mlreview.com/l1-norm-regularization-and-sparsity-explained-for-dummies-5b0e4be3938a#.6gnc3uhdg)
## Why regularization helps overfitting in Neural Networks
- intuition 1: if $\lambda$ is big, the loss function mainly relies on the regularization part, which leads to the weights closer to 0  ($w \approx 0$). And this means that the impact of a lot of hidden units are "zeroing-out", so the neural network is much more simplified, and therefore reducing variance (i.e. reduce overfitting)
- intuition 2: let's assume the activation functions are tanh(). For tanh(), if the z is very close to 0, it is almost a linear function. If $\lambda$ is big, then $w$ is small, then $z = wa + b$ is small, so each layer is almost like a linear layer. And if each layer is a linear layer, the whole network is linear, and won't be able to fit complicated decision boundaries, thus reducing variance (i.e. reduce overfitting)
![[tanh.png]]