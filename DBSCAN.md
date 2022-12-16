#clustering 

## High Level Summary
Density-Based Spatial Clustering of Applications with Noise (DBSCAN) is a clustering algorithm based on the assumption that clusters are dense areas. DBSCAN groups together points that are close to each other based on a distance measurement and a minimum number of points. It also marks as outliers the points that are in low-density regions.

## Detail
### Parameters
- eps: the threshold to consider two points are considered close points (i.e. neighbors)
- minPoints: the minimum number of points to form a dense region
### Clustering process
1. For every data point, obtain the close points from that point (using eps)
2. For every data point with number of close points > minPoints, call them core points
3. Randomly pick a core points and assign to a cluster
	1. Core points close to the selected core point are assign to the same cluster
	2. Continue adding core points until there are no further addable core points
4. Add non core points close to any core points in the cluster
5. Repeat 3-4 with unassigned core points
6. Mark points that are not assigned to any cluster as outliers
### HDBSCAN
HDBSCAN is a hierarchical density-based clustering algorithm. HDBSCAN is basically just an extension of the DBSCAN algorithm that converts it into a hierarchical clustering algorithm.

## Reference
1. DBSCAN https://www.youtube.com/watch?v=RDZUdRSDOok