#LLM  #LLMGenerationConfig
There are two methods to generate response in a LLM after getting the token probability after the Softmax layer.

## Greedy
Select the token with the highest probability

## Weighted sampling
Select the token by doing a random-weighted sampling, where the weight is the corresponding probability of the tokens.

![[LLM_generation_strategy.png]]

## References
- https://www.coursera.org/learn/generative-ai-with-llms/lecture/18SPI/generative-configuration