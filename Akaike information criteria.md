#regression  #evaluate 
- Measure for evaluating and comparing models
- AICc(corrected for small samples), converges to AIC when number of observation increases
- Lowest value is best
- Penalize complex models like Adjusted $R^2$, [[Lasso regression]] and [[ridge regression]], to avoid overfitting to the model
- $\text{AIC} = -2 \ln (L) + 2d$, where $L$ is the likelihood and $d$ is number of features in the model

See more regression evaluation metrics in [[Regression Evaluation Measure]].
## Reference
1. https://towardsdatascience.com/introduction-to-aic-akaike-information-criterion-9c9ba1c96ced
2. https://www.youtube.com/watch?v=-BR4WElPIXg