#optimizer 
## One line summary
Adam Optimizer combines [[Gradient Descent with Momentum]] and [[RMSprop]].
Adam = Adaptive moment estimation

## Detail
On iteration t
	Compute $dw$, $db$ on current mini-batch
	[[Gradient Descent with Momentum]]: Compute [[Exponentially Weighted Moving Averages]] of the gradients: $$v_{dw} = \beta_1 v_{dw} + (1-\beta_1)dw$$$$v_{db} = \beta_1 v_{db} + (1-\beta_1)db$$[[RMSprop]]: Compute [[Exponentially Weighted Moving Averages]] of the square of gradients:$$s_{dw} = \beta_2 s_{dw} + (1-\beta_2)dw^2$$$$s_{db} = \beta_2 s_{db} + (1-\beta_2)db^2$$
	Bias Correction:
	$$v_{dw} = v_{dw} /(1-\beta_1^t), v_{db} = v_{db} /(1-\beta_1^t)$$
	$$s_{dw} = s_{dw} /(1-\beta_2^t), s_{db} = s_{db} /(1-\beta_2^t)$$
	Update weights
	$$w = w - \alpha \frac{v_{dw}}{\sqrt{s_{dw}}}$$
	$$b = b - \alpha \frac{v_{db}}{\sqrt{s_{db}}}$$
## Reference
1. https://www.youtube.com/watch?v=JXQT_vxqwIs&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=22