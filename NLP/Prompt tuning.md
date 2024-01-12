#LLM 
Prompt tuning adds trainable "soft prompt" to inputs. One can consider those soft prompts as "fake words" lying in the embedding space.

![[softprompt.png]]

During prompt tuning, weights of the model is frozen. Therefore, it is more efficient comparing to full fine-tuning.
For different tasks, we only need to train different soft prompt.
![[multitasks_prompt_tuning.png]]
**Interpretability of soft prompts**: because soft prompts are fake words in the embedding space, it is a little bit hard to interpret them. One method is to look at the nearest neighbors in the embedding space to grasp its meanings.

**Note: Prompt tuning is not prompt engineering!**