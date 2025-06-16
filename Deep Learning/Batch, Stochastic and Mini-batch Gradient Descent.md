#optimizer 

## What are they?
Batch Gradient Descent calculate the gradient on the full dataset.

Stochastic Gradient Descent calculate the gradient on one datapoint.

Mini-batch Gradient Descent calculate the gradient on a mini-batch of the dataset.

## Pros and Cons
Batch Gradient Descent is more accurate, and it is more smooth. However, it is more likely to be stuck into a local minima.

Stochastic Gradient is noisy, but has the potential to jump out of a local minima.

Mini-batch Gradient Descent is in between, so potentially achieves best of both worlds.

## Reference
1. https://towardsdatascience.com/https-towardsdatascience-com-why-stochastic-gradient-descent-works-9af5b9de09b8