#NLP 

Tokenization is the foremost step while modeling text data, which is used to prepare a vocabulary. It will also separate a given text into small tokens, which can be later processed by model structures such as RNN, Transformers, etc.




Subword Tokenization


Subword Tokenization splits the piece of text into subwords (or n-gram characters). For example, words like lower can be segmented as "low-er", smartest as "smart-est", and so on.

## Subword Tokenization

## Word-levelTokenization
- The most common type of tokenization, e.g. WhiteSpaceTokenization
- Word2Vec and Glove all uses word-level tokenization
- Disadvantage: 
	- **Out of vocabulary words.** Though we can use "UNK" to replace them, we lose information about those rare words, and they will have the same representation
	- **Vocabulary size.** Vocabulary size can explode with a large corpus

## Character-level Tokenization
- Split a piece of text into a set of characters.
- Handles OOV naturally
- Limit vocabulary (26 characters in English)
- Disadvantage
	- Length of input and output text increases rapidly with character representations
	- Challenging to learn the relationship between the characters to form meaningful words

## Subword-level Tokenization
- Split a piece of text into subwords (or n-gram characters)
	- In between word-level and character-level
	- e.g. lower -> low-er, smartest -> smart-est
- OOV can be segmented as subwords and represents the word in terms of these subwords
- The length of input and output is more manageable comparing to character-level tokenization
- Algorithms
	- [[Byte Pair Encoding (BPE)]]
	- [[SentencePiece]]
	- [[WordPiece]]
	- [[Unigram]]



## Reference
1. https://www.analyticsvidhya.com/blog/2020/05/what-is-tokenization-nlp/
2. https://huggingface.co/docs/transformers/tokenizer_summary#wordpiece