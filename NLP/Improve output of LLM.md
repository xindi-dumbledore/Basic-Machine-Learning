#LLM 
## Chain-of-thought prompting
See [[Prompt Engineering#Chain-of-thought]]
## Sampling outputs
To counteract the randomness of generative model's output, one can ask the generative model to output several answers of the same prompt, and takes the majority result as the final answer.
![[Screenshot 2025-06-15 at 8.21.30 PM.png]]
## Tree-of-thought
Tree-of-thought sampling multiple intermediate "thoughts". The method works as follows. When faced with a problem that requires multiple reasoning steps, it often helps to break it down into pieces. At each step, the generative model is prompted to explore different solutions to the problem at hand. It then votes for the best solution and continues to the next step.
![[Screenshot 2025-06-15 at 8.24.08 PM.png]]
## Emulating conversation between experts
Tree-of-thought is very expensive since we are prompting so many branches. There is one attempt to achieve this by emulating conversation between experts with the following prompt
```python
# Zero-shot tree-of-thought
zeroshot_tot_prompt = [{"role": "user",
"content": "Imagine three different experts are answering this question. All experts will write down 1 step of their thinking, then share it with the group. Then all experts will go on to the next step, etc. If any expert realizes they're wrong at any point then they leave. The question is 'The cafeteria had 23 apples. If they used 20 to make lunch and bought 6 more, how many apples do they have?' Make sure to discuss the results."} ]
```

## Output Verification
LLM output might be connected to downstream applications so output verification is very important. Mostly we want to verify the following aspects:
1. Structured output: for example, we want a JSON format
2. Valid output: e.g. we want to choose from "positive/negative", it shouldn't generate "banana".
3. Ethics
4. Accuracy
### Provide examples
One way to fix output is to provide examples, this usually work for "Structured output" and some of the "valid output".

### Grammar: constrained sampling
Another way to fix for "structured output" and "valid output" is through constrained sampling. 

Packages have been rapidly developed to constrain and validate the output of generative models, like Guidance, Guardrails, and LMQL. In part, they leverage generative models to validate their own output. The generative models retrieve the output as new prompts and attempt to validate it based on a number of predefined guardrails.
![[Screenshot 2025-06-15 at 8.36.07 PM.png]]

This process can be taken one step further and instead of validating the output we can already perform validation during the token sampling process. **When sampling tokens, we can define a number of grammars or rules that the LLM should adhere to when choosing its next token.** For instance, if we ask the model to either return “positive,” “negative,” or “neutral” when performing sentiment classification, it might still return something else. By constraining the sampling process, we can have the LLM only output what we are interested in. Note that this is still affected by parameters such as top_p and temperature.
![[Screenshot 2025-06-15 at 8.36.56 PM.png]]