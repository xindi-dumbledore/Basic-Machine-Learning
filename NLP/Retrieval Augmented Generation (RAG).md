
LLM + external data sources
Using RAG, we don't need to retrain based on new information

RAG is a framework for providing LLMs access to data they did not see during training.

Retriever: Query encoder + External information sources
Query encoder encodes the user prompt to query they external information source (e.g. both the prompt and the document is converted to an embedding)

Retriever returns a group of documents from the data and adds them to the original prompt to create an expanded prompt

The expanded prompt is passed to the LLM to get the answer

Data preparation for RAG
1. Data must fit inside context window
	1. Single document might be too large to fit in the window, so we might need to split long sources into short chunks
2. Data must be in format that allows its relevance to be assessed at inference time
	1. Vector database search