#tree #boosting 

Boosting is an [[Ensemble Modeling]] technique. It improve prediction power by converting a number of weak learners (e.g. shallow [[Decision Tree]]) to strong learners.

In boosting algorithm, we first built a model on the training dataset, then a second model is built to rectify the errors present in the first model. This procedure is continued until the training dataset is perfectly predicted, or the number of models built reaches a preset threshold.

Example algorithms includes [[Gradient Boosting Trees]], [[AdaBoost]], [[XGBoost]]

![[Weak_Learners_web.png]]

## Random notes
1. XGBoost, a variant of GBM, used to be the algorithm of choice for many winning teams of ML competitions. It’s been used in a wide range of tasks from classification, ranking, to the discovery of the Higgs Boson. However, many teams have been opting for LightGBM, a distributed gradient boosting framework that allows parallel learning, which generally allows faster training on large datasets.