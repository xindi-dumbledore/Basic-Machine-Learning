#optimizer 

## One line summary
RMSprop = root mean squared propagation

## Detail
On iteration t
	Compute $dw$, $db$ on current mini-batch
	Compute [[Exponentially Weighted Moving Averages]] of the square of gradients:$$s_{dw} = \beta_2 s_{dw} + (1-\beta_2)dw^2$$$$s_{db} = \beta_2 s_{db} + (1-\beta_2)db^2$$Update weights
	$$w = w - \alpha \frac{dw}{\sqrt{s_{dw}}}$$
	$$b = b - \alpha \frac{db}{\sqrt{s_{db}}}$$
### Why it works
- When gradient is big, our parameters are more likely to oscillate. To prevent oscillation, we want to decrease the learning rate. And when the gradient is big, we would have a bigger $s$, and divide $\alpha$ with a bigger $s$, we would have a smaller learning rate.

## References
1. https://www.youtube.com/watch?v=_e-LFe_igno&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=21