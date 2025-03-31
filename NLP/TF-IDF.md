## Term Frequency (TF)
Denote $f_{ij}$ as Frequency of a term $i$ in document $j$
$$TF_{ij} = \frac{f_{ij}}{\max_k f_{kj}}$$

## Inverse Document Frequency (IDF)
Denote $n_i$ as number of documents that mention term $i$
$N$ as total number of documents
$$IDF_i = \log \frac{N}{n_i}$$
## TF-IDF
$$w_{ij} = TF_{ij} \times IDF_i$$
We can represent a document as the set of words with highest TF-IDF scores, together with their scores. We can then represent the corpus as a `documents x terms` matrix

#feature-extraction #NLP 