#LLM #LLMGenerationConfig

Temperature is a hyperparameter that applies to the final softmax layer of the LLM.
- If the temperature is low (e.g. < 1), the softmax probability distribution is more peaked -> the generated text has lower degree of randomness
- If the temperature is high (e.g. >1), the softmax probability distribution is more flatter -> the generated text has higher degree of randomness

![[LLM_temperature_diagram.png]]

## References
- https://www.coursera.org/learn/generative-ai-with-llms/lecture/18SPI/generative-configuration