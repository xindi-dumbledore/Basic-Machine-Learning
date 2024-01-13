#LLM #finetuning 

![[LLM_finetuning_overview.png]]

The data to fine-tune LLM is prompt/completion pair.

## Fine-tune with Instruction

### Dataset preparation
A common way to structure the fine-tuning data is called **fine-tune with instruction**, where each prompt/completion pair includes a specific instruction to the LLM. This dataset is also called **instruction dataset**. For example:
```
Summarize the following text:
[EXAMPLE TEXT]
Summary: [EXAMPLE COMPLETION]

Translate this sentence to Chinese
Sentence: [EXAMPLE TEXT]
Translation: [EXAMPLE COMPLETION]
```

The fine-tuning can be single task or multi-tasks.
### Fine-tuning process
We then split the instruction dataset into train, validation and test. The rest follows classical machine learning training process. The loss function is depended on the task.

[[Catastrophic Forgetting]]

## References
1. Sample prompt instruction templates: https://github.com/bigscience-workshop/promptsource/blob/main/promptsource/templates/amazon_polarity/templates.yaml