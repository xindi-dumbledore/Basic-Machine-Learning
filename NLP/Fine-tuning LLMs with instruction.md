prompt-completion pairs

instruction fine-tuning
each data includes a instruction such as: summarize the following, translate this sentence to ...

Q: can we mix different instructions together?

full fine-tuning, which updates all parameters in the LLM, is very expensive

1. prepare instruction datasets
2. split the dataset
3. 

Q: what is the training loss for tasks like translation and summarization?

Sample prompt instruction templates
https://github.com/bigscience-workshop/promptsource/blob/main/promptsource/templates/amazon_polarity/templates.yaml

LoRA

fine-tuning on a single task: only 500-1000 examples needed to fine-tune a single task


multi-task instruction fine-tuning might need 500-100,000 examples

FLAN (fine-tuned language net)
- FLAN models refer to a specific set of instructions used to perform instruction fine-tuning

**For each task (e.g. summarization), we have include different instructions (e.g. a) what was going on in that conversation? b) write a summary c) briefly summarize that dialogue)**


Prompt tuning with Soft prompts
- Prompt tuning is not prompt engineering!
- prompt tuning adds additional trainable tokens to your prompt, which is called "soft prompt"


llama-2