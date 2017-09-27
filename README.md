# Recommender Systems for Implicit Feedback: Collaborative Filtering augmented with Side-Information
## Problem Definition
 A common use case is to recommend additional items from an item catalogue to a user.
In coming up with these recommendations, the algorithm underlying the cross-sell/up-sell models must take into account:
* user purchase behavior
* user and item attributes

### Modeling Framework: Combining Collaborative Filtering with Regression
In Collaborative Filtering (CF), the model directly learns from the purchase behavior of users to recommend additional items. It does so by analyzing the relationships between users and interdependencies among items to identify new user-item associations. 


When a user has exhibited sufficient purchase behavior, the CF based approach in general is superior to content based approaches that make predictions based on the user’s observable features [1]. 


Collaborative Filtering based on matrix factorization techniques is now considered state of the art. In this approach, we estimate latent factors per each user and item. These latent factors characterize the user’s unobservable preferences and can be combined with the latent factors of other items in CTL’s inventory to recommend the top items the user is likely to purchase. We can think of these latent factors as the user’s underlying DNA that cannot be directly observed and only inferred from the user’s purchases. 


We propose to customize the algorithm by [2] (supported by Spark’s Machine Learning library) wherein the model learns these latent factors based on implicit feedback derived from the item-user purchase matrix:


![alt text](https://user-images.githubusercontent.com/13146709/30917513-d22d628e-a3b9-11e7-8d39-76e621e420ba.png)

‘1’ indicates that the item is present in the user’s item portfolio. The customization entails augmenting user and item latent factors with the user/item's observable features.

This hybrid approach of combining collaborative filtering with regression confers the following benefits: 

1. It ovecomes the cold-start problem where a user has very few purchases and a purely CF based approach would make poor recommendations 
2. Embedding observable features acts as a sort of regularizer and improves model accuracy.

## References
[1] Y. Koren, R. Bell, and C. Volinsky, “Matrix Factorization Techniques for Recommender Systems”, IEEE Computer Society.

[2] Y.F. Hu, Y. Koren, and C. Volinsky, “Collaborative Filtering for Implicit Feedback Datasets,” Proc. IEEE Int’l Conf. Data Mining (ICDM 08), IEEE CS Press, 2008, pp. 263-272.

[3] S. Rendle, C. Freudenthaler, Z. Gantner, and L. Schmidt-Thieme, “BPR:  Bayesian Personalized Ranking from Implicit Feedback”, UAI, 2009.

