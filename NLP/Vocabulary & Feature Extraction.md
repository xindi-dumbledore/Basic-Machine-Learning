#NLP 

In NLP, the first challenge we encounter is that computers can only handle numbers. Therefore, we need to figure a way to convert text to numbers.

### Word Vector (Bag of Words)
The easiest way to convert text to numbers is word vector. The idea is simple: we first obtain the vocabulary of the corpus $V$, then given a piece of text (e.g. a tweet), we mark the word in this piece of text as 1 and all others as 0, here is an example:
![[word vector.png]]

Problem
- The vector is too sparse, would lead to large training time and large prediction time
	- e.g. if we want to build a logistic regression model using these word vectors as features, we would need to train a logistic regression model with $|V|$ parameters
- It does not consider order of words in a sentence
- The obtained representation does not capture semantic and contexual meaning of the sentence

### Frequency (TF-IDF)
TF-IDF intended to reflect how important a word is to a document in a collection or corpus. TF-IDF normalize the Bag of Words matrix based on frequency.
Problems
- Sparse representation
- Doesn't consider word order
- Still can't capture a lot of semantic and contextual meaning
- A normalization step is needed to recompute term frequencies when a new sentence is added 


### Word Embeddings
#### Word2vec

Word2Vec is a family of models to produce word embeddings. These models use a shallow neural network architecture and utilize the co-occurences of words in a local context to learn word embeddings. In particular, the model learns to predict a center word from its surrounding words during the training phase. After the training phase, the model is capable of converting words into meaningful embeddings.

There are two main models based on word2vec: Continuous Bag of Words (CBOW) and Skip-gram. For details see [[Word2Vec]].

#### Transformer-based models
Transformer consider the context of the words in a sentence when converting them into embeddings. **As opposed to word2vec models, transformer models produce different embeddings for the same word.**
![[Screenshot 2025-04-02 at 08.53.52.png]]
#### Embedding (lookup layer)