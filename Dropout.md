#deep_learning 
## Implementing dropout ("Inverted dropout")
### Training
For every iteration
```
for each layer l:
	d_l = np.random.rand(a_l.shape[0], a_l.shape[1]) < keep_prob
	a_l = np.multiply(a_l, d_l) # zeroing out activations for some neurons according to d_l
	a_l /= keep_prob # normalization, key to inverted dropout
```
Note: we divide the final number by `keep_prob` so that the overall sum of the neuron values remains the same with and without dropout.

### Testing
Don't use dropout

### Implementation Trick
`keep_prob` can vary by layer. For layer with more parameters, we tend to use smaller keep_prob so we have higher regularization effect.

## Why does drop-out work
- Intuition 1: Dropout randomly knocks out units, so for each iteration we are working with smaller neural network, and smaller neural network has some regularization effect
- Intuition 2: For any unit, features from last layer will be randomly knock out, so that the unit can't rely on any one specific feature, and therefore has to spread out the weights for previous features. And by spreading out the weights, it has the effect of shrinking the weights, similar to L2 [[Regularization]]
	- Prevent feature co-adaptation: A feature cannot only be useful in the presence of particular other features
	- Dropout can formally be shown to be an adaptive, feature-dependent version of L2 regularization, but the $\lambda$ will be different for each weight
- Other intuitions
	- Can be thought of as a form of model bagging (Manning, CS224n)

## Reference
1. https://www.youtube.com/watch?v=D8PJAL-MZv8&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=6
2. https://www.youtube.com/watch?v=ARq74QuavAo&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=7
