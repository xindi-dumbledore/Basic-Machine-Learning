#LLM #information-retrieval 

There are three broad categories of use language models for search: dense retrieval, reranking and [[Retrieval Augmented Generation (RAG)]]

## Dense retrieval
The idea of dense retrieval is to convert the problem into **retrieving the nearest neighbors of the search query**. We basically use LLM to transform search query and documents into embeddings, and calculate similarity of text embeddings.

## Reranking
Most search system has a step of reranking, which is mostly followed by dense retrieval. In the reranking step, the input are query and a smaller number of relevant documents, and the goal is to reorder the documents. It is also mostly embedding based.

Example architecture: monoBERT

## RAG
Different from the previous two methods, RAG is a **generative search system**.In RAG, we provide the system with the question (query) and some retrieved results, and LLM will generate the answer, ideally citing the sources we provided. This can help the system to reduce hallucinations, increase factuality, and/or ground the generation model on a specific dataset.

![[Screenshot 2025-06-14 at 10.48.22 PM.png]]