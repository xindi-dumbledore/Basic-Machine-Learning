#NLP
- Language Modeling is the task of predicting what word comes next, e.g. "The students opened their {books, laptops, exams, minds}"
- Given a sequence of words $x^{(1)}, x^{(2)}, ..., x^{(t)}$, compute the probability distribution of the next word $x^{t+1}$, where $x^{(t+1)}$ can be any word in vocabulary $V = \{w_1, ..., w_{|v|}\}$
$$P(x^{(t+1)} | x^{(t)}, ..., x^{(1)})$$
And a system that does this is called a Language Model.
- It can also be regarded as a system that assigns probability to a pice of text $$P(x^{(1)}, x^{(2)}, ..., x^{(T)}) = P(x^{(1)})P(x^{(2)}|x^{(1)})...P(x^{(T)} | x^{(T-1)}, ..., x^{(1)}) = \prod_{t=1}^T P(x^{(t)} | x^{(t-1)}, ..., x^{(1)})$$
- Examples
	- N-gram language models
		- Markov assumption: $x^{(t+1)}$ depends only on preceding $n-1$ words, i.e.
		$$P(x^{(t+1)} | x^{(t), ..., x^{(1)}}) = P(x^{(t+1)} | x^{(t), ..., x^{(t-n+2)}})$$
		- Then we estimate the probability by simply counting
	- Neural language models
		- [[Recurrent Neural Networks (RNN)]]
			- [[LSTM]]
			- [[GRU]]
		- [[Transformer]]
- Evaluating Language Models: [[Perplexity]]
- Why we care about Language Modeling
	- Language modeling is a benchmark task that helps us measure our progress on language understanding
	- Language modeling is a subcomponent of many NLP tasks, especially those involving generating text or estimating the probability of text, e.g. machine translation, text summarization, dialogue, etc.