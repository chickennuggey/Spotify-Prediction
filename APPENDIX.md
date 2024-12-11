1. Explain the exploratory data analysis that you conducted. What was done to visualize your
data and split your data for training and testing?


2. What data pre-processing and feature engineering (or data augmentation) did you complete
on your project?


3. How was regression analysis applied in your project? What did you learn about your data
set from this analysis and were you able to use this analysis for feature importance? Was
regularization needed?


4. How was logistic regression analysis applied in your project? What did you learn about your
data set from this analysis and were you able to use this analysis for feature importance?
Was regularization needed?


5. How were KNN, decision trees, or random forest used for classification on your data? What
method worked best for your data and why was it good for the problem you were addressing?


6. How were PCA and clustering applied on your data? What method worked best for your
data and why was it good for the problem you were addressing?

K-means clustering was used in the data in order to explore underlying patterns related to energy levels of different spoify tracks. We focused on creating clusters using acousticness and energy and were able to obtain 6 distinct clusters, 3 of which were high-enery and 3 of which were low-energy. This was good for our goal since it allowed us to idenify groups of tracks that were considered to be low and high energy. In order to expand on this, it would be interesting to see if there are features that may have contributed to this clustering or to analyze the type of track genres or artists in each cluster. On the otherhand, PCA would not have been as effective, since we are not interested in dimensionality reduction given the fact that the data is not extremely high-dimensional and we want to explore the contribution of each feature to the variabiliy in energy rather than the contribution of the PC to energy. 

8. Explain how your project attempted to use a neural network on the data and the results of
that attempt.

Two neural networks were used, one to predict continuous energy values and one to classify energy levels as low or high. The regression neural network used acousticness and loudness as inputs and obtained a loss of 0.04


10. Give examples of hyperparameter tuning that you applied in preparing your project and how
you chose the best parameters for models.
