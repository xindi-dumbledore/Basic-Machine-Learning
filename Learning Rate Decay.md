#optimizer 
## One line Summary
Slowly reduce learning rate over time (e.g. epochs, or mini-batches) as gradient

## Detail
- Method 1: $\alpha = \frac{\alpha_0}{1 + \text{decay rate} * \text{epoch num}}$
- Method 2: $\alpha = \text{decay rate}^{\text{epoch num}} \alpha_0$
- Method 3: $\alpha = \frac{k}{\sqrt{\text{epoch num}}} \alpha_0$
## References
1. https://www.youtube.com/watch?v=QzulmoOg2JE&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=23