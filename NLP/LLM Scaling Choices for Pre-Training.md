#LLM #pretrain 
LLM pre-training needs balancing between compute budget, model performance, dataset size and model size.
## Model Performance
 Compute budget vs performance: power law(?)
![[compute_budget_vs_performance.png]]
![[model_performance_data_model_size.png]]

## Compute budget
- Measurement: **1 petaflop/s-day** =  number of floating point operations performed at rate of 1 petaFLOP per second for one day
	- 1 petaFLOP/s = 1,000,000,000,000,000 (one quadrillion) floating point operations per second
	- 1 petaflop/s-day is
		- 8 NVIDIA V100s GPUs running at full efficiency for 24 hours
		- 2 NVIDIA A100s GPUs running at full efficiency for 24 hours
- Number of petaflop/s - days to pre-train various LLMs (see Ref 1.)
![[training_petaflops.png]]

## Compute optimal models
- Normally we are given a fixed compute budget. Therefore, the key component we have to balance is the dataset size and the model size. i.e. the important question is: **To train a model with model size x, how big the dataset is needed?**
- Based on Chin
- chilla scaling laws (Ref 3), the compute optimal training data size is ~20x number of parameters
	- the size of the data is measured in number of tokens
- LLaMa and BloombergGPT all used Chinchilla laws to guid their data size

Chinchilla scaling laws for model and dataset size

dataset size = 20x of model parameters
## References
1. Brown et al. 2020, “Language Models are Few-Shot Learners”
2. Kaplan et al. 2020, “Scaling Laws for Neural Language Models”
3. Hoffmann et al. 2022, “Training Compute-Optimal Large Language Models”