#LLM 
## Prompt Engineering Flow Chart
Prompt engineering is empirical, which needs test and iterate often
![[prompt_engineering_iterations.png]]
### Test cases
Test cases is very important because they are the guide to evaluate whether a prompt is good. One thing to pay attention is to include edge cases in the test cases. Common edge cases include:
1. Not enough information to yield a good answer
2. poor user input (typos, harmful, off-topic, nonsense etc.)
3. Overly complex user input
4. No user input

## Prompt Engineering Techniques (a little bit specific to Claude)
### Structure
1. "\\n\\nHuman:"
2. Task context
3. Tone context
4. Background data & documents
5. Detailed task description & rules
6. Examples
7. Conversation history
8. immediate task description or request
9. Thinking step by step/ take a deep breath
10. output formatting
11. "\\n\\nAssistant:"
![[Screenshot 2024-01-12 at 12.43.18 PM.png]]
### General Rules
1. Clear and direct
2. Assign roles
	1. e.g. You are a master logic bot designed to answer complex logic problems.
2. Use XML tags
3. Use structured prompt templates
	1. Parameratize input data
4. Format output
	1. e.g. Use JSON format with the keys as "first_line", "second_line", and "third_line".
2. Speak for Claude
	1. e.g. Assistant:Standalone question:
3. Think step by step
	1. e.g. Directly add "Think step by step" into the prompt
	2. e.g. Before answering, please think about the question within <thinking></thinking> XML tags. Then, answer the question within <answer></answer> XML tags.
4. Use examples (few shot prompting)
	1. Examples should be relevant and have diversity

### Advanced Prompting Techniques
1. Prompt chaining: Separate a complex prompts into different steps
	![[Screenshot 2024-01-12 at 1.07.25 PM.png]]
2. Long context prompts. For long (100K+) prompts:
	1. Put longform input data in XML tags
	2. For document Q&A, ask the question at the end of the prompt
	3. For multiple choice generation: give Claude some example question + answer pairs
	4. Pull out relevant quotes
		1. e.g. Please extract, word-for-word, any quotes relevant to the question
	5. Tell Claude to recite back the details of the task
	6. Give Claude a rubric and ask Claude to check and rewrite its answers based on the rubric
	7. Ask Claude if it understands
		1. Do you understand the instructions? If you do, please repeat them back to me in your own words
		2. Then put Claude's response into the actual prompt
3. Search and [[RAG]]
4. Agents and PAL