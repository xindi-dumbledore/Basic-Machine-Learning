#optimizer 

## One line summary
Compute an exponentially weighted average of the gradients and use that gradient to update the parameters.

## Detail
On iteration t
	Compute $dw$, $db$ on current mini-batch
	Compute [[Exponentially Weighted Moving Averages]] of the gradients: $$v_{dw} = \beta v_{dw} + (1-\beta)dw$$$$v_{db} = \beta v_{db} + (1-\beta)db$$
	Update weights
	$$w = w - \alpha v_{dw}$$
	$$b = b - \alpha v_{db}$$
### Why it works
If the gradient is oscillating (e.g. from positive to negative and to positive), the exponentially weighted moving averages value will be approximately 0. Therefore we don't update the weights that drastically.