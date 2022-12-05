#basic #classification

- Hypothesis$$h(x^{(i)}, \theta) = \text{sigmoid}(\theta ^T x^{(i)})$$where $\text{sigmoid}(x) = \frac{1}{1 + \exp (-x)}$
- Prediction (in real practice, we can use other threshold than 0.5)
$$\hat{y^{(i)}} = h(x^{(i)}, \theta) \geq 0.5$$
![[Pasted image 20221204153103.png]]
- Loss function
$$J(\theta) = -\frac{1}{m} \sum_{i=1}^m[y^{(i)}\log h(x^{(i)}, \theta) + (1-y^{(i)})\log (1-h(x^{(i)}, \theta))]$$