One Sentence Summary

## Algorithm
1. Randomly sample from the hyperparameter space as the current state, and evaluate the performance
2. Alter the current state by randomly updating value of one hyperparameter by sampling a new value in the immediate neighborhood to get neighboring state. If this neighboring state has been visited, resample until getting a new neighboring state. Evaluate the performance on the neighboring state
3. Compare the neighbhoring state and current state performance, and decide whether to accept the neighboring state as current state
	1. If neighboring state better than current state: Accept
	2. If neighboring state worse than current state: Accept with probability $e^{-\beta \Delta f/T}$
		1. $\beta$ is a constant
		2. $T$ is current temperature
		3. $\Delta f$ is the performance difference between the current state and the neighboring state

## Annealing algorithm parameters
1. $\beta$: normalizing constant
	1. Choice of $\beta$ depends on the expected variation in the performance measure over the search space. This can be chosen by playing around with [this](https://github.com/santhoshhari/simulated_annealing/blob/master/simulated_annealing_parameters.xlsx) Excel workbook. If the chosen value of beta is too high, i.e., probability of rejecting a set of parameters is too low in later iterations, you may end up in an infinite loop.
2. $T_0$: initial temperature
	1. A good rule of thumb is that your initial temperature ![](https://latex.codecogs.com/gif.latex?T_0 "T_0") should be set to accept roughly 98% of the moves and that the final temperature should be low enough that the solution does not improve much, if at all
3. $\alpha$: Factor by which temperature is scaled after $n$ iterations
4. $n$: Number of iterations after which temperature is altered
	1. 

## References
https://santhoshhari.github.io/simulated_annealing/