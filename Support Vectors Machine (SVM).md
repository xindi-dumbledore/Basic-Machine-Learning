#basic #classification 
### High Level Summary
Support Vectors Machine (SVC) is a supervised algorithm that aims to find a hyperplane in an N-dimensional space(N — the number of features) that distinctly classifies the data points.

Our objective is to find a plane that has the maximum margin, i.e the maximum distance between data points of both classes. Maximizing the margin distance provides some reinforcement so that future data points can be classified with more confidence.

## Details
### Large Margin Classifier
SVM tries to fit the widest possible hyperplane (decision boundary)  to separate the classes. The decision boundary is fully determined (or supported) by the most extreme instances of the class, and these instances are called support vectors (circled back in the below figure)
![[SVM diagram.png]]

### Why not maximum margin classifier?
A natural idea is that we find the decision boundary that generates the maximum margin possible. However, this is **very sensitive to outliers.** Imagine one instance of class A is very close to class B. Using maximum margin classifier, we will get a decision boundary very close to class B because of that outlier.
![[Pasted image 20221226101502.png]]
### Soft Margin Classifier
To deal with the problem of maximum margin classifier, we want to build a soft margin classifier, which focuses on two objectives:
- Maximize the distance between the decision boundary and support vectors (large margin)
- Maximize the number of points that are correctly classified by the decision boundary

### Kernel Trick
The above discussion is on linearly separable dataset, but that is usually not the case. On these dataset, we want to transform the data into high-dimensional space (by adding more features such as polynomials), where it will become linearly separable. Directly mapping is very costly, but luckily we have the kernel trick to the rescue!



The observations on the edge and within the s#oft margin are called support vectors.

## References
1. https://towardsdatascience.com/machine-learning-algorithms-from-start-to-finish-in-python-svm-d9ff9b48fd1
2. Jure Leskovec: https://www.youtube.com/watch?v=8xbnLHn4jjQ
3. https://stats.stackexchange.com/questions/74499/what-is-the-loss-function-of-hard-margin-svm