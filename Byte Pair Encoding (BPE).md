#NLP
## Learning
1. Split the words in the corpus into characters after appending "\</w\>" to each word
2. Initialize the vocabulary with unique characters in the corpus
3. Compute the frequency of a pair of characters or character sequences in corpus (i.e., compute character n-gram frequency)
4. Merge the most frequent pair in corpus
5. Save the best pair to vocabulary
6. Repeat 3-5 for a certain number of iterations

## Applying on OOV words
1.  Split the OOV word into characters after appending \</w\>
2.  Compute pair of character or character sequences in a word
3.  Select the pairs present in the learned operations
4.  Merge the most frequent pair
5.  Repeat steps 2 and 3 until merging is possible

## Reference
1. https://www.analyticsvidhya.com/blog/2020/05/what-is-tokenization-nlp/