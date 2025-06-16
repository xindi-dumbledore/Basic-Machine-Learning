There are three common types of personalized recommendation systems:
- Content-based filtering
- Collaborative filtering
- Hybrid filtring
![[Screenshot 2025-04-03 at 13.29.34.png]]
## Content-based filtering
This technique uses video features to recommend new videos similar to those a user found relevant in the past. For example, if a user previously engaged with many ski videos, this method will suggest more ski videos.
![[Screenshot 2025-04-03 at 13.30.41.png]]
- User A engaged video X and video Y in the past
- Video Z is similar to X and Y
- System recommends Z to user A

Pros:
- Ability to recommend new videos. With this method, we don't need to wait for interaction data from users to build video profiles for new videos. The video profile depends entirely upon its features.
- Ability to capture the unique interests of users. Since we base the recommendation on user's previous engagement, we are able to personalize for the users
Cons
- Difficult to discover a user's new interests
- Require domain knowledge because we need to process the videos correctly.

## Collaborative filtering
In collaborative filtering, the intuition is that similar users are interested in similar videos.
![[Screenshot 2025-04-03 at 13.39.46.png]]
- We want to find recommendation for user A
- We find user B is similar to user A based on their engagement history
- User B likes video Z which user A hasn't seen
- System recommends Z to user A

Pros:
- No domain knowledge needed. We are not relying on videos.
- Easy to discover users' new area of interest. The system can recommend videos about new topics based on other similar users
- Efficient. CF model is usually faster and less compute-intensive than content-based filtering
Cons:
- Cold start problem.
	- New users don't have enough interaction data available
	- New videos don't have enough exposure
- Can't handle niche interest. For users with niche interest, it might be hard to find similar users.

## Hybrid filtering
Hybrid filtering combined both content-based filtering and collaborative filtering. It can be parallel or sequential. In practice, sequential is used more often.
![[Screenshot 2025-04-03 at 13.44.29.png]]
## Common Architecture for Recommendation Models
### Matrix Factorization
Matrix factorization is the classic method for collaborative filtering. In this method, we decompose the user-video feedback matrix into two lower dimension matrices, the user embeddings matrix and the video embedding matrix. (In some literature, it is also interpreted as user x topic and topic x video). 
![[Screenshot 2025-04-04 at 11.16.28 1.png]]
#### Feedback matrix
To use matrix factorization, we need to curate a user-video feedback matrix. The feedbacks can come from
- explicit feedback: e.g. likes/dislikes, shares, less data more accurate
- implicit feedback: e.g. click, watch time, more data, less accurate
#### Training
During training, the goal is to make the two matrix product as close to the original matrix as possible. The two decomposed matrix was randomly initialized first, then iteratively optimize to decrease the loss.

**Choice of loss function**
- Squared distance over observed <user, video> pairs: this loss function only look at the positive examples in the feedback matrix
	- this loss function didn't penalize bad predictions on unobserved pair, e.g. the matrix with all 1 would have loss = 0
- Squared distance over both unobserved and observed <user, video> pairs: this loss function treats unobserved as 0, and include them into the calculation as well.
	- unobserved is dominated during training because positive labels are sparse, this may lead to all predictions closer to 0
- Weighted combination of unobserved and observed pairs
![[Screenshot 2025-04-04 at 11.21.45 1.png]]
**Optimization**
- Stochastic Gradient Descent: see [[Batch, Stochastic and Mini-batch Gradient Descent]]
- Weighted alternating Least Squares (WALS), which is an [[Expectation Maximization]] algorithm and is specific to matrix refactorization
	- Fix one embedding matrix U and optimize the other embedding V
	- Fix embedding V and optimize U
	- Repeat
#### Inference
We take multiplication of the user embedding matrix and video embedding matrix to get the predicted feedback matrix. Each entry in the predicted feedback matrix can be interpreted as a relevance score.
#### Pros and Cons
Pros
- Fast to train and serve
Cons
- Cold start problem: new users with no historical data 
- Solely rely on user-video interactions, doesn't use other important information such as user features or video features

### Two-tower neural network
In the two-tower neural network, there are two towers: user tower and video tower. The user tower has an user encoder that will convert user features to a user embedding, and the video tower has a video encoder that will convert video features to a video embedding. Finally, the relevance score is computed by the dot product of the two embeddings.
![[Screenshot 2025-04-04 at 11.33.55 1.png]]
#### Training
**Dataset**
To train the two-tower neural network, we need to gather positive and negative <user, video> pairs and their associated features. Positive pairs can be obtained from user feedbacks. Negative pairs can be obtained from sampling from the video pool that doesn't appear in the positive pairs. Pay attention to the data imbalance issue.

**Loss function**
Since the two-tower network output binary labels, it's a classification task. Therefore, we can use cross-entropy as the loss function.
![[Screenshot 2025-04-04 at 11.41.11 1.png]]
#### Inference
- Assuming all videos are embedded and indexed using the video encoder and indexing service
- For a given user, we first get its user embedding using the trained user encoder
- Then we find the nearest neighbor video embeddings of the user embedding using [[Nearest Neighbor Search Algorithms]].
#### Adapted for collaborative filtering

#### Pros and Cons
Pros
- Utilize user and vide features
- Can handle new users
Cons
- Slower training and serving, more expensive