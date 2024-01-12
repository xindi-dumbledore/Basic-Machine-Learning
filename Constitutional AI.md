#LLM 
Constitutional AI is a method for training models using a set of rules and principles that govern the model's behavior. For example, the constitutional principles can be:
![[Screenshot 2024-01-03 at 3.54.28 PM.png]]
# Steps
## Supervised Learning Stage
### Red teaming
Prompt the LLM to generate harmful responses
![[Screenshot 2024-01-03 at 3.54.13 PM.png]]
### Ask the model to critique and revise the harmful responses according to the constitutional principles
![[Screenshot 2024-01-03 at 3.55.13 PM.png]]
### Fine-tune the model using the pairs of red team prompts and revised responses
![[Screenshot 2024-01-03 at 3.55.25 PM.png]]
## Use reinforcement learning to further fine-tune the model
Similar to RLHF, but this time the responses are AI generated, so it's called RLAIF#¬
![[Screenshot 2024-01-03 at 3.55.51 PM.png]]
