#LLM  #LLMGenerationConfig

Top-k and top-p sampling is only valid if the response generation strategy is [[LLM Response Generation Configuration - Sampling Strategy#Weighted sampling]]. They are methods to limit the pool to generate the token.
## Top-k sampling
In top-k sampling, the model selects an output from the top-k tokens with the highest probabilities
![[LLM_top_k_sampling_diagram.png]]
## Top-p sampling
In top-p sampling, we sort the tokens by probability, and the selection pool stops when the cumulative probability <= p. The model then selects an output from the pool with the probability![[LLM_top_p_sampling_diagram.png]]

## References
https://www.coursera.org/learn/generative-ai-with-llms/lecture/18SPI/generative-configuration
