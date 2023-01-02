#designing-ml-systems 
p.g. 205 of *[[Designing Machine Learning Systems]]*

## Advantage of compressing models
- Make the model fit on edge devices
- Make the model smaller often make them run faster

## Method of model compression
- Low-Rank Factorization
	- replace high-dimensional tensors with low dimensional tensors
- Knowledge distillation #todo 
	- Knowledge distillation is a method in which a small model (student) is trained to mimic a larger model or ensemble of models (teacher).
- Pruning
	- Traditionally, decision tree pruning
	- Neural networks
		- Remove entire nodes of a neural network
		- Find parameters least useful to predictions and set them to 0
- Quantization
	- Use fewer bits to represent its parameters, e.g. 32 bits -> floats