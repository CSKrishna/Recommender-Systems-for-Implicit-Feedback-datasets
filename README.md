# Recommender Systems for Implicit Feedback: Collaborative Filtering augmented with Side-Information
## Problem Definition
 A common use case is to build models for cross-sell/up-sell recommendations from an item catalogue to an extant user base.
In coming up with these recommendations, the algorithm underlying the cross-sell/up-sell models must take into account:
* user purchase behavior
* user and item attributes

### Modeling Framework: Combining Collaborative Filtering with Regression
In Collaborative Filtering (CF), the model directly learns from the purchase behavior of users to recommend additional items. It does so by analyzing the relationships between users and interdependencies among items to identify new user-item associations. 
When a user has exhibited sufficient purchase behavior, the CF based approach in general is superior to content based approaches that make predictions based on the user’s observable features [1].
Collaborative Filtering based on matrix factorization techniques is now considered state of the art. In this approach, we estimate latent factors per each user and item. These latent factors characterize the user’s unobservable preferences and can be combined with the latent factors of other items in CTL’s inventory to recommend the top items the user is likely to purchase. We can think of these latent factors as the user’s underlying DNA that cannot be directly observed and only inferred from the user’s purchases.
We propose to customize the algorithm by [2] (supported by Spark’s Machine Learning library) wherein the model learns these latent factors based on implicit feedback derived from the item-user purchase matrix:

