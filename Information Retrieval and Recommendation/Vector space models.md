#information-retrieval 
**Vector space model** or **term vector model** is an algebraic model for representing text documents (or more generally, items) as vectors such that the distance between vectors represents the relevance between the documents. It is used in information filtering, information retrieval, indexing and relevancy rankings.

## Limitations
1. Long documents are poorly represented because they have poor similarity values (a small [scalar product](https://en.wikipedia.org/wiki/Scalar_product "Scalar product") and a [large dimensionality](https://en.wikipedia.org/wiki/Curse_of_dimensionality "Curse of dimensionality"))
	1. Solution: one can chunk long documents into smaller chunks, and represent each chunk as an embedding
2. Search keywords must precisely match document terms; word [substrings](https://en.wikipedia.org/wiki/Substring "Substring") might result in a "[false positive](https://en.wikipedia.org/wiki/False_positive "False positive") match"
3. Semantic sensitivity; documents with similar context but different term vocabulary won't be associated, resulting in a "[false negative](https://en.wikipedia.org/wiki/False_negative "False negative") match".
4. The order in which the terms appear in the document is lost in the vector space representation.
5. Theoretically assumes terms are statistically independent.
6. Weighting is intuitive but not very formal.

https://en.wikipedia.org/wiki/Vector_space_model