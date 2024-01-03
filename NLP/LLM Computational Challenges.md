### What is the problem
- Assumption: Assume we have a model with 1 billion (1B) parameters. Each LLM parameter is in 32-bit full precision.
- In 32-bit full precision, 1 parameter = 4 bytes
- Memory needed to store model: LLM model with 1B parameters = $4 \times 10^9$ bytes = 4GB
- Memory needed to train model: To train such a model, there needs about ~20 extra bytes per parameter (Ref 1.), which takes about $4 * 20 = 80$ GB
	- ![[additional_RAM_training_breakdown.png]]
![[memory_needed_large_models.png]]
## How to solve the problem
### Quantization
- Quantization: projects number with high precision into low precision spaces
- By losing some precision of the parameter, we can reduce the memory needed.
- Quantization-aware training (QAT) learns quantization scaling factors during training
- BFLOAT16 is a popular choice

![[quantization_diagram.png]]

![[quantization_memory.png]]

### Multi-GPU Compute
- For extremely large models or large training data, we need to distribute the compute to multiple GPUs.
	- Model too big for single GPU
	- Model fits on GPU, train data in parallel
- Common strategies
	- Distributed Data Parallel (DDP)
		- Only distribute data. LLM fully copied on each GPU.
	- [[Full Sharded Data parallel (FSDP)]] - "ZeRO" paper (zero data overlap between GPUs)
		- Distributing (sharding) model parameters, gradients and optimizer states across GPUs.

### Balance Model size and dataset size 
See [[LLM Scaling Choices for Pre-Training]]

## References
1. https://huggingface.co/docs/transformers/v4.20.1/en/perf_train_gpu_one#anatomy-of-models-memory