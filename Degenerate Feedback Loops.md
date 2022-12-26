#LTR #designing-ml-systems #recommender-systems

A degenerate feedback loop can happen when the predictions themselves influence the feedback, which, in turn, influences the next iteration of the model.

Degenerate Feedback Loops are common in ranking and recommender systems. **Items ranked high by the system are shown first to users, and users tend to click on them more, which makes the system more confident that these recommendations are good.**

It is also called position bias/popularity bias/selection bias in recommender systems and learning to rank.

Degenerate feedback loops will cause system's outputs to be more homogeneous over time.

## Detecting degenerate feedback loops
- Measure popularity diversity of a system
	- Popularity: how many times an item has been interacted with
	- Metrics
		- Aggregate diversity
		- Average coverage of long-tail items
- Measure hit rate
	- Divide items into buckets based on popularity
	- Measure prediction accuracy of a recommender system for each of the buckets. If the prediction accuracy is lower on less popular items, it likely suffers from popularity bias
## Correcting degenerate feedback loops
- Introduce randomization
	- e.g. in Tiktok, each new video is randomly assigned an initial pool of traffic. This pool of traffic is used to evaluate each video's unbiased quality to determine whether it should be moved to a bigger pool of traffic or be marked as relevant
- Positional features
	- This will allow the model to learn how much being at each position influences how likely it is going to be clicked on.
	- modeling choices
		- numerical positions
		- whether it is the first position or not
	- During inference, set the positional features as default
- Inverse propensity scoring (more specific to Learning to Rank, Joachims 2017)
	- Weight clicks to correct for position bias
	- Decompose click probability: for an item $d$ and a rank $k$ $$P(C = 1|k, d) = P(E = 1|k)P(C=1|E=1, d)$$, $C = 1$ means the item is clicked, $E = 1$ means the item is examined. $P(E = 1|k)$ is called examination propensity and $P(C=1|E=1, d)$ is called relevance
	- Estimate relevance as follows, where $c_i(d)$ is the number of clicks: $$relevance(d) \approx \frac{1}{N} \sum_{i=1}^N \frac{c_i(d)}{P(E=1|k)}$$
	- Estimate examination propensity
		- swap intervention experiment


## Reference
1. Unbiased Learning-to-Rank with Biased Feedback: https://arxiv.org/pdf/1608.04468.pdf