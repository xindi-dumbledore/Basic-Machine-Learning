Nearest neighbor search algorithms is a core component for information retrieval, search and recommendation systems.
## Exact nearest neighbor
Brute force approach: calculate distance between query $q$ and each item in the index table, and retrieve the $k$ nearest points. The time complexity is $O(N \times D)$, where $N$ is the total number of points and $D$ is the point dimension. It is accurate but very slow in large-scale system.
## Approximate nearest neighbor (ANN)
In production, ANN is more practical. There are many variations of ANN.

### Tree-based ANN
Partition the space by the tree, and when we search NN, only look in the partition $q$ belongs to.
### Locality-sensitive hashing (LSH)-based ANN
Use LSH to map data points into different buckets. Only look in the same bucket $q$ belongs to.
### Clustering-based ANN
Grouping the points based on similarities. Only look in the same cluster $q$ belongs to.
## Hierarchical navigable small world (HNSW)
One famous ANN method is called HNSW.
### H is for Hierarchical: Skip Lists
In HNSW we use multi-layer graph. The top layer is the most sparse, and each layer gets more dense with nodes until we get to the bottom layer. If a node is on a given layer, the same node is also in the layer below it. Whenever we insert new vectors into the database, we index the data in this probabilistic way. The probability of a vector being assigned to a given layer becomes exponentially smaller as you go up the hierarchy.
### NSW is for Navigable Small Worlds graphs
After we select which layer the vector goes onto, we connect this vector to other vectors that are nearest to it on that layer.

When adding a new node, the algorithm performs a greedy search in the existing structure to find the closest nodes in higher layers. This search starts from an entry point at the highest layer and progressively moves down, layer by layer, until it finds the best candidates for connections in each relevant layer. This process ensures that the new node is well integrated into the existing network, preserving the small-world properties.

As more nodes are added, the network dynamically updates, always seeking to maintain efficient paths between nodes. This may involve adding or adjusting connections not just for new nodes but occasionally for existing ones as well to preserve the network’s navigability.

### Search
1. **Starting the search:** The ANN search begins at the top layer of the HNSW graph, which has the fewest nodes (vectors). The aim is to find a node that serves as a good entry point because it’s close to the query vector in the vector space.
2. **Gathering candidates:** As the search progresses to lower layers, it’s not just about finding a single vector closest to the query. The algorithm collects a set of candidate vectors that are close to the query vector, effectively gathering a “pool” of potential nearest neighbors.
3. **Choosing the top 5 candidates:** At each layer, the algorithm evaluates the distances between the query vector and the vectors in the candidate pool. If a vector is found to be closer than the current candidates, it is included in the pool, potentially replacing a farther candidate to maintain the pool size (e.g. top 5 closest vectors). This dynamic updating process ensures that only the closest vectors are retained as the search progresses.
4. **Knowing when to stop:** Determining when to stop the search is one of the challenges of this algorithm. The hyperparameter is used to set the size of the dynamic candidate list, which affects both accuracy and search time. The search ends when further exploration fails to find closer vectors.
HNSW can achieve logarithmic time complexity, which is very important in large scale system

# Reference
1. HNSW: https://medium.com/@wtaisen/hnsw-indexing-in-vector-databases-simple-explanation-and-code-3ef59d9c1920