#designing-ml-systems #data

p.g. 113 of *[[Designing Machine Learning Systems]]*
Data augmentation is a family of techniques that are used to increase the amount of training data. Traditionally, these techniques are used for tasks that have limited training data, such as in medical imaging. However, in the last few years, they have shown to be useful even when we have a lot of data—augmented data can make our models more robust to noise and even adversarial attacks.

## Simple Label-Preserving Transformations
- Computer vision
	- cropping, flipping, rotating, inverting (horizontally or vertically), erasing part of the image, etc. while preserving the labels
- NLP
	- randomly replace a word with a similar word
	- similar word can be found in a dictionary or synonymous words, or finding words whose embeddings are close to each other in a word embedding space

## Perturbation
- Neural networks are sensitive to noises. By adding noisy samples to the training data can help the neural network become more robust.
- Computer vision
	- Add random noise or by search strategy
	- Adversarial augmentation
		- e.g. DeepFool: finds the minimum possible noise injection needed to cause a misclassificcation with high confidence
- NLP
	- e.g. BERT chooses 15% of all tokens in each sequence at random and chooses to replace 10% of the chosen tokens with random words
	- Adversarial augmentation is less common
## Data Synthesis
- Computer vision
	- Combine existing examples with discrete labels to generate continuous labels
	- Mix a dog picture and a cat picture with some weights, and also generate the label with the weights
- NLP
	- Use templates
![[NLP template synthesis.png]]