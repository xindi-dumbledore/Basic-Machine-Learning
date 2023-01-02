#designing-ml-systems #to-do
p.g. 183 of *[[Designing Machine Learning Systems]]*

Model calibration is a subtle but crucial concept to grasp. Imagine that someone makes a prediction that something will happen with a probability of 70%. What this prediction means is that out of all the times this prediction is made, the predicted outcome matches the actual outcome 70% of the time. If a model predicts that team A will beat team B with a 70% probability, and out of the 1,000 times these two teams play together, team A only wins 60% of the time, then we say that this model isn’t calibrated. A calibrated model should predict that team A wins with a 60% probability.

To measure a model’s calibration, a simple method is counting: you count the number of times your model outputs the probability X and the frequency Y of that prediction coming true, and plot X against Y.

![[calibration plots.png]]