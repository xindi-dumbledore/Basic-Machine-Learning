#designing-ml-systems 

p.g. 104 of *[[Designing Machine Learning Systems]]*

## Problem of Class Imbalance
- There is insufficient signal for your model to learn to detect the minority classes
- Makes it easier for your model to get stuck in a non-optimal solution by exploiting a simple heuristic instead of learning anything useful about the underlying pattern of the data
	- e.g. 99.99% of data is not cancer, if your model always output not cancer, it achieves 99.99% accuracy already, and it's hard to get better
- Leads to asymmetric costs of error: the cost of wrong prediction on a sample of the rare class might be much higher than a wrong prediction on a sample of the majority class
	- e.g. misclassification on X-ray with cancer is much more dangerous than misclassifiction on X-ray without cancer

## Handling Class Imbalance
- Using the right evaluation metrics [[Classification Evaluation Measures]]
	- don't use accuracy, use precision, recall and F1
	- precision, recall and F1 are asymmetric metrics, which means that their values depending on which class is considered the positive class, so calculate for both class
- Resampling
	- Undersampling majority class
		- e.g. [[Tomek links]], find pairs of samples from opposite classes that are close in proximity and remove the samples of the majority class in each pair
		- might lose important data from removing data
	- Oversampling for minority class
		- e.g. SMOTE (synthetic minority oversampling technique), synthesizes novel examples of the minority class through sampling convex combinations of existing data points within the minority class
		- might overfitting on the training data, especially the new data are replicas of existing data
	- Other sampling techniques
		- two-phase learning: train the model on resampled data, fine-tune the model on original data
		- dynamic sampling: oversample low-performing classes and undersample the high-performing classes during the training process
- Manipulate model loss function
	- giving the training instances we care about higher weight, we can make the model focus more on learning these instances
	- Cost-sensitive learning
		- Define a cost matrix for each class and their outcome, and weight the loss based on the cost matrix
![[cost_matrix.png]]
	- Class-balanced loss
		- punish the model for making wrong predictions on minority classes
		- weight each class's loss by $N/\text{number of samples of class }i$
	- Focal loss
		- let model focus on learning the samples it still has difficulty classifying
		- Adjust the loss so that if a sample has lower probability of being right, it'll have a higher weight
- Ensemble methods have shown to help with imbalance problem