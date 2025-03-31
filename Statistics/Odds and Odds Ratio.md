#statistics 

## Odds
- In English, it is common to say things like "my team's odds of winning is 5 out of 3"
- Odds are just ratio of something happening to something not happening, can be calculated from counts or probability, $$\text{Odds} = \frac{p}{1-p}$$
- Log of odds $\log (\text{Odds})$
	- Odds are between $[0,\infty]$, below 1 means the team is "losing", and higher than 1 means the team is more likely to "win". It is asymmetrical.
	- Taking the log will make it symmetric, between $[-\infty, \infty]$, and 1/6 odds and 6/1 odds will be of the same magnitude
- If I pick pairs of random numbers that add up to 100, and use them to calculate the log(odds) and draw a histogram, the histogram is in the shape of a normal distribution

## Odds Ratio
- Ratio of odds of two things, e.g. $$ \text{Odds(event 1)} = \frac{p_1}{1 - p1}$$ $$ \text{Odds(event 2)} = \frac{p_2}{1 - p2}$$
$$ \text{Odds Ratio} = \frac{\text{Odds(event 1)}}{\text{Odds(event 2)}}$$
- Log of Odds Ratio simply takes log over the odds ratio to make it symmetric
- Usage of Odds Ratio: indicate a relationship between two things
	- Example: we can use an "odds ratio" to determine if there is a relationship between the mutated gene and cancer
		- If the person have mutated gene, the odds they have caner is 23/117
		- If the person doesn't have mutate gene, the odds they have caner is 6/210
		- the odds ratio is (23/117)/(6/210) = 6.88
		- the log of odds ratio is 1.93
		- larger value mean that mutate gene is a good predictor of cancer and vise versa
![[odds ratio example.png]]
- Determine whether odds ratio is statistically significant
	- Fisher's Exact Test
	- Chi-Square Test
	- The Wald Test
		- Commonly used to determine the significance of odds-ratios in [[Logistic Regression]] and to calculate confidence intervals
		- Use the fact that the log(odds ratio) forms a norm distribution, then we can check where the observed log(odds ratio) is on the distribution
## References
1. https://www.youtube.com/watch?v=ARfXDSkQf1Y
2. https://www.youtube.com/watch?v=8nm0G-1uJzA