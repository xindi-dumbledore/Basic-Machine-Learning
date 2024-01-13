Example prompts includes

- Question: problem to solve
	- e.g. Which magazine was started first, Arthur's Magazine or First for Women?
- Thought: a reasoning step that identifies how the model will tackle the problem and identify an action to take
	- e.g. I need to search Arthur's Magazine and First for Women and find which one was started first.
- Action: An external task that the model can carry out from an **allowed set of actions**
	- e.g. pool is
		- search(entity)
		- lookup(string)
		- finish(answer)
	- search(Arthur's Magazine)
- Observation: the result of carrying out the action

Repeat the Thought - Action - Observation cycle as many times as necessary to get the final answer