#dimension-reduction 

## High level summary
Uniform Manifold Approximation and Projection (UMAP) takes high-dimensional data and outputs a low-dimensional graph, and preserve the high-dimensional clusters and their relationship to each other.

## Details

### General idea
Initialize the low dimensional points and then move the low dimensional points around until they form clusters that have the same relationships we saw in the high-dimensional data.

### Algorithm
Number of high dimensional neighbors each point should have $n$
1. Calculate raw distances between each pair of data
2. Calculate high-dimensional similarity score of all data relative to a selected point $X$ $e^{-(\text{raw dist to X} - \text{dist to nearest neighbor of X})}/\sigma$, choose $\sigma$ so that the sum of the scores equal to $\log_2(n)$
3. Making the scores symmetrical for each pair: $S = (S_1 + S_2) - S_1S_2$ (fuzzy union)
4. Initialize initial low-dimensional graph using spectral embedding
5. Calculate low-dimensional similarity scores: $\frac{1}{1 + \alpha d^{2\beta}}$, where $d$ is the low dimensional distance
6. Moving the low-dimensional points


## Reference
1. https://www.youtube.com/watch?v=eN0wFzBA4Sc
2. https://www.youtube.com/watch?v=jth4kEvJ3P8