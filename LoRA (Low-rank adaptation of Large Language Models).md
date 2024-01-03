- Train two low-rank small matrix in the self-attention layer
- For different tasks, we can train different low rank matrices and keep the LLM original weights frozen.
- How it can save space
	- Base Transfomer model presented by Vaswani et al. 2017 have transformer weights dimension as $d \times k = 512 \times 64 = 32768$ parameters
	- Assume we train LoRA with rank $r = 8$
		- Matrix A has dimensions $r \times k = 8 \times 64 = 512$ parameters
		- Matrix A has dimensions $d \times r = 512 \times 8 = 4096$ parameters
		- Total number of parameters = 4608, which is about 14%  of the 32768 parameters
- How to choose rank
	- There seems to be a plateau of performance of the rank of the small matrix. 
	- 4-32 should be fine. 
	- We should try them to find the best rank
![[LoRA_diagram.png]]
- QLoRA: Quantized LoRA

## References
- Hu et al. 2021, "LoRA: Low-Rank Adaptation of Large Language Models"
- Dettmers et al. 2023, "QLoRA: Efficient Finetuning of Quantized LLMs"