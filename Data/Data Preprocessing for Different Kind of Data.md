## Numerical
- Scaling: make range between 0 to 1
- Standardization: make mean 0 and variance 1
- Take logarithm: mostly on heavy-tailed distribution
- Make into buckets: e.g. we might want to split age into different buckets
## Categorical
- Ordinal: if the category have intrinsic order, map them into integer that preserve the order
- One-hot encoding: but if there are too many categories, might not be a good choice.
- Learn some embedding: if there are too many categories, learn embedding to represent each category
## Text
- Lowercase letter
- Remove stopwords, punctuation etc.
- Stemming, Lemmatization
- Tokenization
- Vectorization: convert text into numerical values, see [[Vocabulary & Feature Extraction]]
	- direct encode
	- bag of words, tf-idf etc.
	- word embeddings
## Image
- Resize: fixed image sizes
- Scaling: scale pixel values of the image to be between 0-1
- Z-score normalization: scale pixel values to have a mean of 0 and variance of 1
- Consistent of color: ensure images have consistent color mode (e.g. RGB or CMYK)
- Use pre-trained model to convert image into embedding

## Video