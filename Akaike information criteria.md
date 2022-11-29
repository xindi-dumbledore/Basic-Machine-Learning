#regression 
- Measure for evaluating and comparing models
- AICc(corrected for small samples), converges to AIC when number of observation increases
- Lowest value is best
- Penalize complex models like [[Adjusted $R2$]], [[Lasso regression]] and [[ridge regression]], to avoide overfitting to the model
- $\text{AIC} = -2 \ln (L) + 2k$, where $L$ is the likelihood and $k$ is number of parameters in the model

https://towardsdatascience.com/introduction-to-aic-akaike-information-criterion-9c9ba1c96ced
https://www.youtube.com/watch?v=-BR4WElPIXg