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
![[Screenshot 2024-01-03 at 3.25.27 PM.png]]
### Prepare labeled data for training
1. Convert rankings into pairwise training data for the reward model
![[Screenshot 2024-01-03 at 3.26.31 PM.png]]
### Train reward model
1. Reward model is a model that given a prompt and completion pair, generate a reward value (i.e. we are scoring the prompt-completion pair whether it is aligned with our alignment criterion)
2. Using the pairwise training data, train reward model to predict preferred completion from $\{y_j, y_k\}$ for prompt $x$
![[Screenshot 2024-01-03 at 3.27.26 PM.png]]
### Use the reward model to fine-tune LLM with RL
![[Screenshot 2024-01-03 at 3.30.01 PM.png]]
![[Screenshot 2024-01-03 at 3.29.44 PM.png]]
## Scaling human feedback
- Collecting human feedback is expensive
- [[Constitutional AI]]
