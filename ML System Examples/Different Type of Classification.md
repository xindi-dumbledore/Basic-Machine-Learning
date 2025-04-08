## Multi-class classification
Multi-class classification is simply we have more than one class, and the **class are mutually exclusive**. E.g.,
- Binary class: cat, dog
- Multi-class: cat, dog, bird

**Loss function**
The loss function for multi-class classification is categorical cross entropy loss (see [[Common Loss Function Glossary#Categorical Cross Entropy]])

## Multi-label classification
In multi-label classification, each data point can have multiple label, rather than just one class. That is to say, the **labels are not mutually exclusive**. E.g.,
- An news article can belong to sports, crime, and entertainment

**Loss function**
The loss function for multi-label classification is a **summation of all binary cross entropy loss** for each label. Because essentially, each label can be considered as a binary classification.

## Multi-task classification
In multi-task classification, we are solving multiple classification problems at the same time, where **each problem (or "task") has its own label space.** For each task, it can be binary classification, multi-class classification or multi-label classification. **In more general multi-task learning, tasks can be other machine learning criteria such as regression.**

In multi-task classification, it's common to have multiple "heads" for each task at later stage of the model. And at early stages, there will be some shared features across different tasks. E.g.
- Task 1: predict candidate's job role (multi-class: data scientist, PM, etc.)
- Task 2: predict seniority level (multi-class: junior, mid, senior)
- Task 3: predict whether they have a PhD (binary: yes/no)

**Loss function**
The loss function for multi-task classification is the **sum of all the loss function for each task**. The loss function of each task depends on the nature of the task.
