#LLM 

During the [[Reinforcement Learning from Human Feedback (RLHF)]], the fine-tuned LLM might "cheat" in order to get high reward completions, but those completions might have low quality. For example, in the figure below, to get low toxicity, the RL-updated LLM generated "Beautiful love and world peace all around" which has low toxicity but has nothing to do with the prompt. This is called Reward Hacking.
![[Screenshot 2024-01-03 at 3.40.12 PM.png]]
To avoid reward hacking, we can use a reference model to gauge the RL-updated LLM. We can calculate a KL divergence ([[Common Loss Function Glossary#Kullback-Leibler (KL) Divergence]]) shift penalty between the reference model and RL-updated LLM, and add this to the reward generated by the reward model. In this way, we keep a balance that the completion shouldn't be too far from the original model, but also more aligned to human feedback.
![[Screenshot 2024-01-03 at 3.41.29 PM.png]]