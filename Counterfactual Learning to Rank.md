#LTR

Optimize a ranking model that matches the user preferences between items, based on historically logged user clicks

Problem: Clicks are biased indicators of preference [[Degenerate Feedback Loops]]


### Solutions
- Inverse propensity scoring
	- Weight clicks to correct for position bias
	- Decompose click probability: for an item $d$ and a rank $k$ $$P(C = 1|k, d) = P(E = 1|k)P(C=1|E=1, d)$$, $C = 1$ means the item is clicked, $E = 1$ means the item is examined. $P(E = 1|k)$ is called examination and $P(C=1|E=1, d)$ is called relevance
	- Estimate relevance as follows, where $c_i(d)$ is the number of clicks: $$relevance(d) \approx \frac{1}{N} \sum_{i=1}^N \frac{c_i(d)}{P(E=1|k)}$$

## Reference
1. https://arxiv.org/pdf/1608.04468.pdf