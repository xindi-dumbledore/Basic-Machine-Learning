#LLM 

## Basic prompt
Basic prompt just send the LLM a sequence without any instructions. In this setting, LLM will simply try to complete the sentence

## Instruction-based prompting
Basically, we want to give LLM detailed instructions on what we want it to achieve. In this way, LLM can accomplish various different tasks.

There are several techniques:
- Specificity: accurately describe what you want to achieve. E.g. "Write a description for a product" -> "Write a description for a product in less than two sentences and use a formal tone."
- Hallucination: to avoid hallucination, we can ask the LLM to only generate an answer if it knows the answer. If it does not know the answer, it can respond with "I don’t know."
- Order: either begin or end your prompt with the instruction. Research has found that information in the middle is often forgotten.
- Persona: Describe what role the LLM should take on. For example, use “You are an expert in astrophysics” if you want to ask a question about astrophysics.
- Context: Additional information describing the context of the problem or task. It answers questions like “What is the reason for the instruction?”
- Format: The format the LLM should use to output the generated text. Without it, the LLM will come up with a format itself, which is troublesome in automated systems.
- Audience: The target of the generated text. This also describes the level of the generated output. For education purposes, it is often helpful to use ELI5("Explain it like I'm 5").
- Tone: The tone of voice the LLM should use in the generated text. If you are writing a formal email to your boss, you might not want to use an informal tone of voice.
- Data: The main data related to the task itself.
![[Screenshot 2025-06-15 at 8.13.49 PM.png]]
## In-context learning
In-context learning is basically providing examples in the prompt. It is also sometimes called one-shot (provide one example) or few-shot (provide multiple examples) prompting.
![[Screenshot 2025-06-15 at 8.15.14 PM.png]]
## Chain Prompting
We can also take the output of one prompt and use it as input for the next prompt, creating a continuous chain of interactions that solves a complex problem.

![[Screenshot 2025-06-15 at 8.17.33 PM.png]]
## Chain-of-thought
Chain-of-thought aims to have the generative model “think” first rather than answering the question directly without any reasoning. This has shown to be effective to increase the reasoning ability for generative models.
![[Screenshot 2025-06-15 at 8.16.34 PM.png]]

Chain-of-thought can also be done without examples (i.e. zero-shot chain-of-thought), and the most famous one is to add the phrase "Let's think step-by-step" in the prompt.
![[Screenshot 2025-06-15 at 8.18.29 PM.png]]