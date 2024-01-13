#LLM 
Constitutional AI is a method for training models using a set of rules and principles that govern the model's behavior. For example, the constitutional principles can be:
![[constitutional_ai.png]]
# Steps
## Supervised Learning Stage
### Red teaming
Prompt the LLM to generate harmful responses
![[reward_hacking_2.png]]
### Ask the model to critique and revise the harmful responses according to the constitutional principles
![[constitutional_ai_2.png]]
### Fine-tune the model using the pairs of red team prompts and revised responses
![[constitutional_ai_3.png]]
## Use reinforcement learning to further fine-tune the model
Similar to RLHF, but this time the responses are AI generated, so it's called RLAIF#¬
![[constitutional_ai_4.png]]
