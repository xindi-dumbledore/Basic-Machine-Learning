#clustering #unsupervised 

K-means is an unsupervised clustering algorithm which utilizes Expectation Maximization. The algorithm is as follows:
![[K-Means_Clustering_web.png]]
## Select Number of clusters $k$
Using the "elbow" or "knee of a curve" as a cutoff point is a common heuristic in mathematical optimization to choose a point where diminishing returns are no longer worth the additional cost. In clustering, this means one should choose a number of clusters so that adding another cluster doesn't give much better modeling of the data.

We can use elbow plot to select the optimal number of clusters. To do that, we calculate two metrics:
- Distortion: average distances between the cluster centerpoints
	- this is also the cost function of K-means
- Inertia: sum of distances between each data point to the assigned cluster centerpoints
Here are two examples:
![[elbow_distorthion.png]]
![[elbow_intertia.png]]
From the above two figures, $k=3$ is at the elbow point, so the optimal $k$ is 3.


## References
1. https://www.geeksforgeeks.org/elbow-method-for-optimal-value-of-k-in-kmeans/
2. https://en.wikipedia.org/wiki/Elbow_method_(clustering)