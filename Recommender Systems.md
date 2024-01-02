## Content-based Recommender Systems
- Represent each item as a feature vector, for example for a movie, we have a feature vector $(x_1, x_2)$, where $x_1$ represents romance and $x_2$ represents action
- then treat user's interaction with the movie as the interaction with the features. So basically, how much weight a user gives for romance ($x_1$) and action ($x_2$)
- Transfer this problem to a regression problem, basically predicting user's rating given the item's features
- Cons
	- We usually don't have item features
	- but I guess if it's podcast, we can get the transcript or description, we can come up with embedding features

## Collaborate Filtering
- Since getting the item features is not easy, we can initialize them randomly at first

### Collaborate Filtering with SVD
Given user x movie rating matrix, we can use SVD to decompose it to

user x concept matrix, concept strength matrix and movie x concept matrix

then to recommend, we can find similar movie to user's previous highly rated movies



## Cold-start problem
- interview the user to get some data to start with
- having some user profile (age, area), and initiate as the average of user's profile


## Other approaches
BERT4Rec: https://towardsdatascience.com/build-your-own-movie-recommender-system-using-bert4rec-92e4e34938c5

## Reference
1. https://www.youtube.com/watch?v=9siFuMMHNIA&list=PL3ZVX5cUMdLbiFgitZszhnMUZHDDEL0rS&index=2