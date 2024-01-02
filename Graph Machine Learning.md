### Traditional ML for Graphs

Given an input graph, extract node, link and graph-level features, learn a model (SVM, neural networks) that maps features to labels

### Graph Representation Learning
Rather than manual feature engineering, we automatically learn the features. Efficient task-independent feature learning for machine learning with graphs. Map node into embeddings, that nodes with close embeddings are similar to each other.

![[Pasted image 20230130094306.png]]
![[Pasted image 20230130094723.png]]

## Random Walk Approaches for Node Embedding
Vector $z_u$: embedding of node $u$
Probability $P(v|z_u)$: the predicted probability of visiting node $v$ on random walks starting from node $u$, given the learned embedding $z_u$

### DeepWalk

### Node2Vec
use flexible, biased random walks that can trade off between local (BFS) and global (DFS) views of the network.

Biased 2nd-order random walk
At each time step, one can choose
- going back to the node it just came from
- go to a node with the same distance as the previous node
- go to a node farther from the previous node