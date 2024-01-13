#LLM
## Why we need to align the model with human feedback
- Bad model behaviors
	- Toxic language
	- Aggressive responses
	- Dangerous information
- We want the model to be Helpful, Honest and Harmless (HHH)

## Process
### Collecting human feedback
1. Given different prompts, collect various model completions (i.e. responses) for each prompt using the Instruct LLM.
2. Define the model alignment criterion (eg. helpfulness), let human labeler to rank the different responses for each prompt.
![[RLHF1.png]]
### Prepare labeled data for training
1. Convert rankings into pairwise training data for the reward model
![[RLHF2.png]]
### Train reward model
1. Reward model is a model that given a prompt and completion pair, generate a reward value (i.e. we are scoring the prompt-completion pair whether it is aligned with our alignment criterion)
2. Using the pairwise training data, train reward model to predict preferred completion from $\{y_j, y_k\}$ for prompt $x$
![[RLHF3.png]]
### Use the reward model to fine-tune LLM with RL
![[RLHF5.png]]
![[RLHF4.png]]
## Scaling human feedback
- Collecting human feedback is expensive
- [[Constitutional AI]]
