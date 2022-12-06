#NLP 

In NLP, the first challenge we encounter is that computers can only handle numbers. Therefore, we need to figure a way to convert text to numbers.

### Word Vector
The easiest way to convert text to numbers is word vector. The idea is simple: we first obtain the vocabulary of the corpus $V$, then given a piece of text (e.g. a tweet), we mark the word in this piece of text as 1 and all others as 0, here is an example:
![[word vector.png]]

Problem
- The vector is too sparse, would lead to large training time and large prediction time
	- e.g. if we want to build a logistic regression model using these word vectors as features, we would need to train a logistic regression model with $|V|$ parameters

### Frequency 


### Word Embeddings
word2vec