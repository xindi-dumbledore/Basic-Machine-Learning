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
Matrix factorization is the classic method for collaborative filtering. In this method, 