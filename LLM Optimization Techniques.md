### Distillation
Train a smaller student model from a larger teacher model.
Student model learns to statistically mimic the behavior of the teacher model.

Process
- Freeze the teacher model and generate completions for the training data with temperature $T < 1$ to the softmax function, which is called soft labels
- Generate completions for the training data using the student model using both $T<1$ (soft predictions) and $T=1$ (hard predictions)
- Distillation loss: calculated using the probability distribution over the tokens between the teacher model and the student label
- Student loss: calculated using hard predictions from the student model and the ground truth labels
- Combine both Distillation loss and student loss to update the student model
Notes
- In practice, distillation is not as effective for generative decoder models
- It is more effective for encoder only models like BERT
### Quantization
Reduce precision of model weights. Similar to [[LLM Computational Challenges#Quantization]]
### Pruning
- Remove model weights with values close or equal to zero
- Pruning methods
	- Full model re-training
	- [[Parameter Efficient Fine-tuning (PEFT)]]
	- Post-training
- In practice, only a small percentage in LLMs are zero-weights so it might have low impact

![[Screenshot 2024-01-03 at 4.48.27 PM.png]]