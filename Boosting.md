#tree #boosting 

Boosting is an [[Ensemble Modeling]] technique. It improve prediction power by convertin a number of weak learners to strong learners.

In boosting algorithm, we first built a model on the training dataset, then a second model is built to rectify the errors present in the first model. This procedure is continued until the training dataset is perfectly predicted, or the number of models built reaches a preset threshold.

Example algorithms includes [[GradientBoostingTrees]], [[AdaBoost]], [[XGBoost]]

![[Weak_Learners_web.png]]