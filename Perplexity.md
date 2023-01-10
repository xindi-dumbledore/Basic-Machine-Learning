#NLP 

Perplexity in general is a measurement of how well a probability model predicts a sample. In NLP, perplexity is one way to evaluate [[Language Modeling]].

Given a corpus to evaluate on, for each sentence $s_i$ in the corpus:
- We calculate the probability of this sentence given the language model $P(s_i)$
- Normalize the probability by the number of words in the sentence, more specifically we use the geometric mean: $P(s_i) ^{1/n}$
- Perplexity of this sentence is the inverse of this number $(\frac{1}{P(s_i)})^{1/n}$
- To calculate perplexity of the whole corpus, we first get the probability of the whole corpus $P(s_1, s_2, ...,s_m) = \prod_{i=1}^m p(s_i)$,
- Then we take the same geometric mean and reverse $(\frac{1}{P(s_1,s_2, ...,s_m)})^{1/n}$

## References
1. https://medium.com/nlplanet/two-minutes-nlp-perplexity-explained-with-simple-probabilities-6cdc46884584