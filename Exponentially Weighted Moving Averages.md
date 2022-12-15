#statistics

$$v_0 = 0$$
$$v_t = \beta v_{t-1} + (1-\beta) a_t$$
$v_t$ can be viewed as approximately average over $\frac{1}{1-\beta}$ timesteps of value
- The higher the $\beta$, the smoother the curve it will be, but it has a latency of change
- The lower the $\beta$, the curve is more jittering, but it is more sensitive to change
- The "exponential" is because we have a exponentially decayed weight on each previous data point
	- e.g. $v_{100} = 0.1 a_{100} + 0.1 \times 0.9 a_{99}, 0.1 \times (0.9)^2 a_{98} + 0.1 \times (0.9)^3 a_{97} + ...$
- Computationally less expensive to calculate averages
### Bias Correction of Exponentially Weighted Moving Averages
- First value is biased because $v_0 = 0$, and it propagates to later time steps.
- Mostly happens at early timesteps
- do $$\frac{v_t}{1-\beta^t}$$
## References
1. https://www.youtube.com/watch?v=NxTFlzBjS-4&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=18
2. https://www.youtube.com/watch?v=lWzo8CajF5s&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=19