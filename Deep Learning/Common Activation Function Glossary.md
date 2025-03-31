#basic #deep_learning #neural_network 

The primary role of the Activation Function is to transform the summed weighted input from the node into an output value to be fed to the next hidden layer or as output. **The purpose of an activation function is to add non-linearity to the neural network.** Without activation functions, our neural network would just be a linear regression model.

![[activation function.png]]

Though linear activation functions and step activation function is mathematically possible, they are not very useful for real applications. Below we only list non-linear activation functions.

## Sigmoid/Logistic Function
It is commonly used as the output layer activation function for binary classifications.
![[Sigmoid_Activation_Function_web.png]]
## Softmax Function
It is most commonly used as an activation function for the last layer of the neural network in the case of multi-class classification. It calculates the relative probabilities. Similar to the sigmoid/logistic activation function, the SoftMax function returns the probability of each class.

![[Softmax_Activation_Function_web.png]]
## Tanh Function
It is usually used in hidden layers.
![[TanH_Activation_Function_web.png]]
$$\phi(z) = \frac{e^z - e^{-z}}{e^z + e^{-z}}$$
## ReLU Function
- It is usually used in hidden layers.
- Since some neurons will be drag to 0, only some neurons will be activated, so it will be more computationally efficient
- Dying ReLU Problem: negative part of the function has gradient 0, some neuron's parameters will not be updated
![[ReLU_Activation_Function_web.png]]
## Leaky ReLU
- Solves the Dying ReLU problem
- Have another straight line for the negative values
![[Leaky_ReLU_web.png]]
## Exponential Linear Units (ELUs)
- Another variant of ReLU that modifies the slope of the negative part of the function to solve the Dying ReLU Problem
![[ELUs_web.png]]
## SoftPlus Function
- Smooth and differentiable near 0
![[Softplus_Function_web.png]]
## Noisy ReLU
![[Noisy_ReLU_web.png]]
## Output Layer Activation Functions
Output layer activation functions is related to the task, here are some common choices:
- Binary classification: Sigmoid
- Multiclass Classification: Softmax
- Regression: no activation function

## References
1. https://www.v7labs.com/blog/neural-networks-activation-functions