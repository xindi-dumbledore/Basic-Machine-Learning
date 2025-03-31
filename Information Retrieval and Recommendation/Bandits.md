#designing-ml-systems 
p.g. 287 of *[[Designing Machine Learning Systems]]*
- Bandit algorithms originated in gambling. A casino has multiple slot machines with different payouts. A slot machine is also known as a one-armed bandit, hence the name. You don’t know which slot machine gives the highest payout. You can experiment over time to find out which slot machine is the best while maximizing your payout.
- Multi-armed bandits are algorithms that allow you to balance between exploitation (choosing the slot machine that has paid the most in the past) and exploration (choosing other slot machines that may pay off even more).
- When you have multiple models to evaluate, each model can be considered a slot machine whose payout (i.e., prediction accuracy) you don’t know. Bandits allow you to determine how to route traffic to each model for prediction to determine the best model while maximizing prediction accuracy for your users.
- Bandits are well-studied in academia and have been shown to be a lot more data efficient than A/B testing (in many cases, bandits are even optimal). Bandits require less data to determine which model is the best and, at the same time, reduce opportunity cost as they route traffic to the better model more quickly. See discussions on bandits at LinkedIn, Netflix, Facebook, and Dropbox, Zillow, and Stitch Fix. For a more theoretical view, see Chapter 2 of Reinforcement Learning (Sutton and Barto 2020).

## Contextual Bandits as an Exploration Strategy
- Contextual bandits are to determine the payout of each action. In the case of recommendations/ads, an action is an item/ad to show to users, and the payout is how likely it is a user will click on it.
- Imagine that you’re building a recommender system with 1,000 items to recommend, which makes it a 1,000-arm bandit problem. Each time, you can only recommend the top 10 most relevant items to a user. In bandit terms, you’ll have to choose the best 10 arms. The shown items get user feedback, inferred via whether the user clicks on them. But you won’t get feedback on the other 990 items. This is known as the partial feedback problem, also known as bandit feedback. You can also think of contextual bandits as a classification problem with bandit feedback.
- Contextual bandits are algorithms that help you balance between showing users the items they will like and showing the items that you want feedback on. 36It’s the same exploration–exploitation trade-off that many readers might have encountered in reinforcement learning. Contextual bandits are also called “one-shot” reinforcement learning problems. 
- Contextual bandits are well researched and have been shown to improve models’ performance significantly (see reports by Twitter and Google).

## Bandits Algorithms Example
- $\epsilon$-greddy
	- For a percentage of time, say 90% of the time or ε = 0.9, you route traffic to the model that is currently the best-performing one, and for the other 10% of the time, you route traffic to a random model. This means that for each of the predictions your system generates, 90% of them come from the best-at-that-point-in-time model.
- Thompson Sampling
	- Thompson Sampling selects a model with a probability that this model is optimal given the current knowledge. In our case, it means that the algorithm selects the model based on its probability of having a higher value (better performance) than all other models.
- Upper Confidence Bound (UCB)
	- UCB selects the item with the highest upper confidence bound. We say that UCB implements optimism in the face of uncertainty, it gives an “uncertainty bonus,” also called “exploration bonus,” to the items it’s uncertain about.

## Reference
1. Greg Rafferty, “A/B Testing—Is There a Better Way? An Exploration of Multi-Armed Bandits,” Towards Data Science, January 22, 2020, https://towardsdatascience.com/a-b-testing-is-there-a-better-way-an-exploration-of-multi-armed-bandits-98ca927b357d #todo 
2. Deep Bayesian Bandits: Exploring in Online Personalized Recommendations: https://arxiv.org/abs/2008.00727
3. AutoML for Contextual Bandits https://arxiv.org/abs/1909.03212