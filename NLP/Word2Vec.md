#feature-extraction #embedding

## Continuous Bag of Words (CBOW)
CBOW predicts the target-word based on its surrounding words.

CBOW thus smoothes over the distribution of the information as it treats the entire context as one observation. CBOW is a faster algorithm than skipgrams and works well with frequent words.
![[Screenshot 2025-04-02 at 08.54.03.png]]
## Skip-gram
Skipgram works in the exact opposite way to CBOW. Here, we take an input word and expect the model to tell us what words it is expected to be surrounded by.

The statistical interpretation of this is that we treat each context-target pair as a new observation. Skipgrams work well with small datasets and can better represent less frequent words.
![[Screenshot 2025-06-16 at 10.19.46 AM.png]]