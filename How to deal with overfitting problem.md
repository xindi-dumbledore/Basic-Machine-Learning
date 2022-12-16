#trick

- Get more training data
- Always have validation set to evaluate performance and do hyperparameter tuning
- [[Regularization]]
- [[Dropout]]
- Others
	- Data augmentation: i.e. get more training data
		- e.g. in CV flipping image, random distortions
		- e.g. in NLP 
	- Early stopping: stop when the dev set is not optimizing anymore
		- couples the tasks of optimizing and prevent overfitting (harm the orthogonalization between optimizing cost function J and prevent overfitting)
		- advantage: we don't need to try different hyperparameters (e.g. $\lambda$ in L2 norm)

## Reference
1. https://www.youtube.com/watch?v=BOCLq2gpcGU&list=PLkDaE6sCZn6Hn0vK8co82zjQtt3T2Nkqc&index=8