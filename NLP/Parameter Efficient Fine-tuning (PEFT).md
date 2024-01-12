#LLM 
Full fine-tuning of large LLMs is challenging. Fine-tuning the whole model requires not only saving trainable weights, but also saving temp memory, forward activations, gradients, optimizer states, which can be 12-20x the size of the weights themselves.

The idea of Parameter Efficient Fine-tuning (PEFT) is that we don't need to fine-tune the full model, but just a small portion of it would be enough. PEFT can be realized by only tuning several final layers of LLM, reparameterize or adding a new layer on top of a LLM.

Additionally, PEFT could save space for multiple models for different use-cases. Consider the base LLM as a bag, PEFT model works as an accessory. We only need to change the PEFT layer for a different use-case.

There are different methods of PEFT
- Selective: Select subset of initial LLM parameters to fine-tune
- Reparameterization: Reparameterize model weights using a low-rank representation
	- [[LoRA (Low-rank adaptation of Large Language Models)]]
- Additive: Add trainable layers or parameters to model
	- Adapters
	- Soft Prompts: [[Prompt tuning]]
