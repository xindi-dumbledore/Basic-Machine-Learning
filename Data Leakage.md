#designing-ml-systems #data 
p.g. 135 of *[[Designing Machine Learning Systems]]*

Data leakage refers to the phenomenon when a form of the label “leaks” into the set of features used for making predictions, and this same information is not available during inference.

## One Example
Suppose you want to build an ML model to predict whether a CT scan of a lung shows signs of cancer. You obtained the data from hospital A, removed the doctors’ diagnosis from the data, and trained your model. It did really well on the test data from hospital A, but poorly on the data from hospital B.

After extensive investigation, you learned that at hospital A, when doctors think that a patient has lung cancer, they send that patient to a more advanced scan machine, which outputs slightly different CT scan images. Your model learned to rely on the information on the scan machine used to make predictions on whether a scan image shows signs of lung cancer. Hospital B sends the patients to different CT scan machines at random, so your model has no information to rely on. We say that labels are leaked into the features during training.

## Common Causes for Data Leakage
- Splitting time-correlated data randomly instead of by time
	- To prevent future information from leaking into the training process and allowing models to cheat during evaluation, split your data by time, instead of splitting randomly, whenever possible. For example, if you have data from five weeks, use the first four weeks for the train split, then randomly split week 5 into validation and test splits
	- E.g.
		- When building models to predict the future stock prices, you want to split your training data by time, such as training your model on data from the first six days and evaluating it on data from the seventh day.
		- Consider the task of predicting whether someone will click on a song recommendation. Whether someone will listen to a song depends not only on their music taste but also on the general music trend that day. If an artist passes away one day, people will be much more likely to listen to that artist. By including samples from a certain day in the train split, information about the music trend that day will be passed into your model, making it easier for it to make predictions on other samples on that same day.
- Scaling before splitting
	- always split your data first before scaling, then use the statistics from the train split to scale all the splits, so that we don’t accidentally gain information about the test split.
- Filling in missing data with statistics from the test split
	- using only statistics from the train split to fill in missing values in all the splits.
- Poor handling of data duplication before splitting
	- If you have duplicates or near-duplicates in your data, failing to remove them before splitting your data might cause the same samples to appear in both train and validation/test splits.
	- If you have duplicates or near-duplicates in your data, failing to remove them before splitting your data might cause the same samples to appear in both train and validation/test splits.
- Group leakage
	- A group of examples have strongly correlated labels but are divided into different splits.
	- This type of leakage is common for objective detection tasks that contain photos of the same object taken milliseconds apart—some of them landed in the train split while others landed in the test split.
	- It’s hard avoiding this type of data leakage without understanding how your data was generated.
- Leakage from data generation process
	- e.g. whether a CT scan shows signs of lung cancer is leaked via the scan machine

## Detecting Data Leakage
- Measure the predictive power of each feature or a set of features with respect to the target variable (label). 
	- If a feature has unusually high correlation, investigate how this feature is generated and whether the correlation makes sense.
- Do ablation studies to measure how important a feature or a set of features is to your model. 
	- If removing a feature causes the model’s performance to deteriorate significantly, investigate why that feature is so important.
- Keep an eye out for new features added to your model. 
	- If adding a new feature significantly improves your model’s performance, either that feature is really good or that feature just contains leaked information about labels.
- Be very careful every time you look at the test split. 
	- If you use the test split in any way other than to report a model’s final performance, whether to come up with ideas for new features or to tune hyperparameters, you risk leaking information from the future into your training process.