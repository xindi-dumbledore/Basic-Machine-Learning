#evaluate 
ROUGE score is mostly used for text summarization, where it compares the generated summaries to one or more reference summaries.

### ROUGE-n
$$\text{ROUGE-n recall} = \frac{\text{n-gram matches}}{\text{n-gram in references}}$$
$$\text{ROUGE-n precision} = \frac{\text{n-gram matches}}{\text{n-gram in generation}}$$
$$\text{ROUGE-n F1} = 2\times\frac{\text{precision} \times \text{recall}}{\text{precision} + \text{recall}}$$
### ROUGE -L
ROUGE-L is calculated on the number of tokens in longest common subsequences (LCS).
$$\text{ROUGE-L recall} = \frac{\text{LCS}(\text{generated},\text{references})}{\text{unigram in references}}$$
$$\text{ROUGE-L precision} = \frac{\text{LCS}(\text{generated},\text{references})}{\text{unigram in generation}}$$
### ROUGE Hacking and ROUGE Clipping
![[ROUGE Clipping.png]]