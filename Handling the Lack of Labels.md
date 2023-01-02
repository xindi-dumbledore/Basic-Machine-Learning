#designing-ml-systems 

There are four techniques for handling the lack of hand-labeled data. (pg. 94 of *[[Designing Machine Learning Systems]]*)

## Weak Supervision
- Leverages (often noisy) heuristics to generate labels
- Write a labeling function (LF) to decode the heuristics
	- Keyword heuristics
		- e.g. if the nurse's note mentions pneumonia, label the patient's case as emergent
	- Regular expressions
		- e.g. if the note matches or fails a certain regular expression
	- Database lookup
		- e.g. if the note contains the disease listed in the dangerous disease list
	- The outputs of other models
		- e.g. if an existing system classifies this as emergent
## Semi-supervision
- Generate new labels from existing labels
- Require having a small number of initial ground-truth labels
- Method 1 Self training
	- training a model on your existing set of labeled data and use this model to make predictions for unlabeled examples
- Method 2 Similarity labeling
	- data samples that share similar characteristics share the same labels
- Method 3 Perturbation-based method, related to [[Data Augmentation]]
	- Apply small perturbations to the training instances to obtain new training instances
		- e.g. adding white noise to images
		- adding small random values to embeddings of words
- Need to pay attention to how much this limited set of ground-truth should be used to evaluate multiple candidate models and select the best one
## Transfer Learning
- Leverage models pretrained on another task for the new task
- Most prevalent in the field of NLP
## Active Learning
- Improving the efficiency of data labels by labeling data samples (mostly human annotating) that are most useful for the model according to some metrics or heuristics
	- uncertainty measurement, label the examples that your model is the least certain about
	- disagreement among multiple candidate models, train an ensemble of models, and label the examples that disagree the most
	- highest gradient or highest loss reduction, select samples that will give the highest gradient updates or will reduce the loss the most