#LLM #information-retrieval 

To turn common search system into a RAG system, we add an LLM to the end of the search pipeline. We present the question and the top retrieved documents (usually chunked first then saved to vector store, so when we retrieve we are retrieving short document chuncks) to the LLM, and ask it to answer the question given the context provided by the search results.

This generation step is called grounded generation because the retrieved relevant information we provide the LLM establishes a certain context that grounds the LLM in the domain we are interested in.

The way we incorporate the retrieved relevant information is basically include them into the prompt sending to the LLM. See below figure for the full pipeline.

![[Screenshot 2025-06-14 at 10.55.01 PM.png]]

## Advanced RAG Techniques
There are several additional techniques to improve the performance of RAG systems.

**Query rewriting**
If the RAG system is a chatbot, the preceding simple RAG implementation would likely struggle with the search step if a question is too verbose, or to refer to context in previous messages in the conversation. This is why it’s a good idea to use an LLM to rewrite the query into one that aids the retrieval step in getting the right information.

An example of this is a message such as:
> User Question: “We have an essay due tomorrow. We have to write about some animal. I love penguins. I could write about them. But I could also write about dolphins. Are they animals? Maybe. Let’s do dolphins. Where do they live for example?”

This should actually be rewritten into a query like:
> Query: “Where do dolphins live”

This rewriting behavior can be done through a prompt (or through an API call).

**Multi-query RAG**
The next improvement we can introduce is to extend the query rewriting to be able to search multiple queries if more than one is needed to answer a specific question. For example:
>User Question: “Compare the financial results of Nvidia in 2020 vs. 2023” 

We may find one document that contains the results for both years, but more likely, we’re better off making two search queries:
>Query 1: “Nvidia 2020 financial results” Query 2: “Nvidia 2023 financial results”

**Multi-hop RAG**
A more advanced question may require a series of sequential queries. Take for example a question like:

User Question: “Who are the largest car manufacturers in 2023? Do they each make EVs or not?” To answer this, the system must first search for:

Step 1, Query 1: “largest car manufacturers 2023” Then after it gets this information (the result being Toyota, Volkswagen, and Hyundai), it should ask follow-up questions:

Step 2, Query 1: “Toyota Motor Corporation electric vehicles” Step 2, Query 2: “Volkswagen AG electric vehicles” Step 2, Query 3: “Hyundai Motor Company electric vehicles”

**Query routing**
An additional enhancement is to give the model the ability to search multiple data sources. We can, for example, specify for the model that if it gets a question about HR, it should search the company’s HR information system (e.g., Notion) but if the question is about customer data, that it should search the customer relationship management (CRM) (e.g., Salesforce).

**Agentic RAG**
You may be able to now see that the list of previous enhancements slowly delegates more and more responsibility to the LLM to solve more and more complex problems. This relies on the LLM’s capability to gauge the required information needs as well as its ability to utilize multiple data sources. This new nature of the LLM starts to become closer and closer to an agent that acts on the world. The data sources can also now be abstracted into tools. We saw, for example, that we can search Notion, but by the same token, we should be able to post to Notion as well.

## RAG Evaluation
RAG system can be evaluated from four different perspectives:
- Fluency: whether the text is fluent and cohesive
- Perceived utility: whether the answer is helpful and informative
- Citation recall: The proportion of generated statements about the external world that are fully supported by their citations.
- Citation precision: The proportion of generated citations that support their associated statements.
- Faithfulness: whether the answer is consistent with the provided context
- Answer relevance: how relevant the answer is to the question

Usually human evaluation is preferred, but we can also use LLM-as-a-judge to conduct this evaluations.