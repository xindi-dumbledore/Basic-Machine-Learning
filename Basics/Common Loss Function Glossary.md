#basic 
## Regression
### Mean Squared Error
Also called L2 loss. It penalizes heavier large errors, but is less robust to outliers.$$MSE = \frac{1}{m}\sum_i^m(y_i - \hat{y}_i)^2$$
### Mean Absolute Error
Also called L1 loss. It is more robust to outliers, but it is not differentiable at 0 $$MAE = \frac{1}{m}\sum_i^m |y_i - \hat{y}_i|$$
### Huber Loss
Combine both MSE and MAE. For loss values less than delta, use MSE; for loss values greater than delta, use MAE.

$$L_{\delta}(y_i \hat{y}_i) = \begin{cases}\frac{1}{2}(y - \hat{y}_i)^2, \text{ for} |y_i - \hat{y}_i| \leq \delta \\ \delta (|y_i - \hat{y}_i| - \frac{1}{2}\delta), \text{ otherwise}\end{cases}$$
## Classification
## Cross Entropy Loss
Also called log loss, logistic loss, multinomial logistic loss.

$$-\sum_{c=1}^M y_{o, c}\log(p_{o,c})$$
M is the number of classes
$y_{o, c}$ is the binary indicator (0 or 1) for observation $o$ and class $c$
$p_{o,c}$ is the predicted probability for observation $o$ and class $c$.

If M = 2, which means binary classification, the above function reduced to
$$-[y \log(p) + (1-y) \log(1-p)]$$where $y$ and $p$ is the actual and predicted probability for class 1 (or 0, as they are symmetric).
### Categorical Cross Entropy
Categorical cross entropy is also called softmax loss. It is used when the label `y` is one-hot encoded (e.g. `[1, 0, 0], [0, 1, 0]` etc.). When used in neural networks, we usually apply a softmax activate function to the neural network last input, then apply the cross-entropy loss.

Tensorflow function can be found [here](https://www.tensorflow.org/api_docs/python/tf/keras/losses/CategoricalCrossentropy)

#### Sparse Categorical Cross Entropy
When use the above formula, the $y_{o,c}$ is expected to be one-hot encoded vector over the categories, which can be very big when the number of classes is big. In Spare Categorical Cross Entropy, we can send in class index as $y_{o, c}$ (e.g. 1, 2, 3 to represent three classes). See [Sparse Categorical Cross Entropy.](https://www.tensorflow.org/api_docs/python/tf/keras/losses/SparseCategoricalCrossentropy)

### Kullback-Leibler (KL) Divergence
Also called relative entropy. Classically used to measure how one probability distribution $P$ is different from a second reference probability distribution $Q$. Following the notation in cross entropy, KL divergence can be calculated as

$$\sum_{c = 1}^M (y_{o,c} \log y_{o,c} - y_{o,c} \log p_{o,c} )= \text{Cross Entropy}(y, p) - \text{Entropy}(y)$$
Tensorflow function can be found [here](https://www.tensorflow.org/api_docs/python/tf/keras/losses/KLDivergence)

### Hinge Loss
Mostly used in [[Support Vectors Machine (SVM)]]
![[Hinge_Loss_web.png]]
![[hinge loss.png]]
## Zero-One Loss (more like an evaluation metric)
$$L_{0-1}(y_i, \hat{y}_i) = I(\hat{y}_i \neq y_i)$$ which simply count wrong predictions (closely related to accuracy)

Zero-one loss is not differentiable, therefore we cannot use methods such as gradient descent.

## Hamming Loss (more like an evaluation metric)
Hamming loss is a generalization of the 0-1 loss to multiple classes
Hamming loss is most useful for multi-label classifications, where a data point can belong to multiple classes.
![[hamming loss multi-label.png]]
## Contrastive Losses
Contrastive losses are commonly used in representation learning, e.g. we want to learn some images so that we can find similar images (see [[01. Visual Search System]]). The main idea is that after getting the embeddings, we want to push embeddings of similar items close to each other, and embeddings of dissimilar embeddings further to each other. There are a lot of variations of contrastive losses.
### The original contrastive loss
Suppose we have some input samples $\{x_i\}$ (e.g. images) and each has a corresponding label $y_i \in \{1, ..., M\}$ among $M$ classes. We learn an embedding function $f_{\theta}$ that encodes $x_i$ into an embedding vector $e_i$. We choose a distance function (e.g. euclidean distance, cosine distance, etc.) $D(e_i, e_j)$ that will calculate the distance between the embeddings for $e_i$ and $e_j$. Then we can write the contrastive loss as:
$$L(x_i, x_j) = \mathbb{1}[y_i = y_j]D(e_i, e_j) + \mathbb{1}[y_i \neq y_j]\max(0, \epsilon - D(e_i, e_j))$$
The first part is used when $x_i$ and $x_j$ belongs to the same class, then we want to minimize the distance between them. The second part is used when $x_i$ and $x_j$ belongs to different class, then we want to maximize the distance between them. But we don't need to push them TOO far, so we define $\epsilon$, we are satisfied enough when $D(e_i, e_j)$ is larger than $\epsilon$.
### Triplet Loss
Triplet loss was originally proposed in FaceNet to learn face recognition of the same person at different poses and angles.
In triplet loss, we have one anchor input $x$ and we select one positive sample $x^+$ and one negative example $x^-$. What we want to achieve is to minimize the distance between $x$ and $x^+$, and maximize the distance between $x$ and $x^-$:
$$ L = \sum_x max(0, D(x, x^+) - D(x, x^-) + \epsilon)$$
## N-pair Loss
Multi-class N-pair loss generalizes triplet loss to include comparison with multiple negative samples.

## Other "Loss" Functions (metrics)
### Gini impurities
Used in [[Decision Tree]]. It's used in a greedy fashion, rather than usual machine learning process (initialize weights, evaluate loss/metric, then use gradient descent to update the weights).

## References
1. https://machinelearningmastery.com/cross-entropy-for-machine-learning/
2. https://towardsdatascience.com/understanding-the-3-most-common-loss-functions-for-machine-learning-regression-23e0ef3e14d3
3. https://towardsdatascience.com/why-is-cross-entropy-equal-to-kl-divergence-d4d2ec413864
4. https://www.linkedin.com/pulse/hamming-score-multi-label-classification-chandra-sharat/
5. https://petamind.com/common-loss-functions-and-their-use-quick-note/
6. https://www.baeldung.com/cs/ai-0-1-loss-function
7. https://towardsdatascience.com/under-the-hood-using-gini-impurity-to-your-advantage-in-decision-tree-classifiers-9be030a650d5
8. Contrastive loss: [https://lilianweng.github.io/posts/2019-11-10-self-supervised/](https://lilianweng.github.io/posts/2019-11-10-self-supervised/).