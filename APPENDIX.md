1.  Explain the exploratory data analysis that you conducted. What was done to visualize your
    data and split your data for training and testing?

        Since our goal was to predict energy based on other variables of songs, we first explored the average energy per genre and visualized this in a table that showed the numeric average energy for each genre in the dataset. We also visualized the energy per genre with a box-whisker plot. Additionally, to evaluate which numeric variables had the highest correlation with energy, we created a correlation matrix and saw that loudness and acousticness had the highest correlations. We also created density plots where high energy is 1 and low energy is 0 to see the distribution over the numeric variables like popularity, danceability, etc., and barcharts for the categorical variables. We split our data into 70% training and 30% testing.

2.  What data pre-processing and feature engineering (or data augmentation) did you complete on your project?

        For preprocessing, we first checked our dataset for missing values and found one row with missing data so we removed that row. We prepared our input features by dropping categorical variables that we were not going to be evaluating. Our target variable was energy. We also standardized our numeric input features by scaling to ensure they were normalized for later use in regularization.

3.  How was regression analysis applied in your project? What did you learn about your data
    set from this analysis and were you able to use this analysis for feature importance? Was
    regularization needed?

        We used both LAD and LS regression models to help predict the energy level. These models had a pretty high correlation and R2 score, with little difference between their training and testing sets. We tried to add some regularization to the model to analyze feature importance and handle multicollinearity. Using lasso regression with an arbitrary L1 penalty term, we can see that the model has diminished all other features except for loudness and acousticness, indicating that these are the most important predictors for the model. This aligns with the correlation matrix, and supports the idea of using only these two predictors for our neural network to avoid overfitting. We then used cross-validation to select the best hyperparameter, but the evaluation metrics did not improve much from our baseline models after L1 regularization. Similarly, adding ridge regression with an L2 penalty term also did not affect our model much, so regularization is not necessary for our regression model.

4.  How was logistic regression analysis applied in your project? What did you learn about your
    data set from this analysis and were you able to use this analysis for feature importance?
    Was regularization needed?

        We used logistic regression to predict whether the energy level of a song was high or low. First, we needed to define what this meant, as energy is a continuous variable. We decided to split the data in half, so the tracks with energy values above the median would be classified as "high" (1), and the remaining tracks would be classified as "low" (0). Now that we have a categorical variable, we can use logistic regression to predict the probability of the energy level for a track in our test set. We used a different subset of features than in LAD/LS regression, as we added some other categorical variables like time signature and key. The prediction accuracy was pretty high, and the specificity was higher than the sensitivity, meaning the proportion of low energy observations correctly predicted by our model was higher than the proportion of high energy observations correctly predicted. Our ROC curve provides a very large AUC, meaning our predictive potential is very high. This implied that further regularization would not be necessary, as the model is already very good at distinguishing between high and low energy levels given the current features as predictors.

5.  How were KNN, decision trees, or random forest used for classification on your data? What
    method worked best for your data and why was it good for the problem you were addressing?

        We used KNN on the energy feature to classify whether a song's energy level is high or low based on its loudness and acousticness. We did this by getting the median value of the energy column to be the threshold for “high” or “low” energy level. We used the loudness and acousticness columns as predictors and split the data into training and testing sets to train and evaluate the model’s performance. The training set was 70% and the testing set was 30%. This method seemed to work best for our data as the ROC curve for KNN 15 had a high AUC 0.91, and KNN 1 had AUC of 0.85, which are both close to 1. From calculating the confusion matrix, we also found that the prediction accuracy was 0.9998 for knn1. KNN was good for the problem we were addressing since we had a very clear decision boundary, and the dataset was not too big. Additionally, we were evaluating only a few features.

6.  How were PCA and clustering applied on your data? What method worked best for your
    data and why was it good for the problem you were addressing?

        K-means clustering was used in the data in order to explore underlying patterns related to energy levels of different spoify tracks. We focused on creating clusters using acousticness and energy and were able to obtain 6 distinct clusters, 3 of which were high-enery and 3 of which were low-energy. This was good for our goal since it allowed us to identify groups of tracks that were considered to be low and high energy. In order to expand on this, it would be interesting to see if there are features that may have contributed to this clustering or to analyze the type of track genres or artists in each cluster. On the otherhand, PCA would not have been as effective, since we are not interested in dimensionality reduction given the fact that the data is not extremely high-dimensional and we want to explore the contribution of each feature to the variabiliy in energy rather than the contribution of the PC to energy.

7.  Explain how your project attempted to use a neural network on the data and the results of
    that attempt.

        Two neural networks were used, one to predict continuous energy values and one to classify energy levels as low or high. The regression neural network used acousticness and loudness as inputs and obtained a relatively low MSE loss of 0.025 for both the validation and testing data after 100 epochs. There was no drastic gap between the training and validation loss. The classification neural network used loudness, acousticness, liveness, valence, key, mode and time_signature as inputs and obtained a relatively high classification accuracy of 82% for both the training and validation data and a binary cross entropy loss around 0.38 for both as well. This shows that the model is quite good at predicting and classifying the energy, but there are simpler models that can achieve the same classification accuracy and are much simpler (logistic regression, knn).

8.  Give examples of hyperparameter tuning that you applied in preparing your project and how
    you chose the best parameters for models.

        For the lasso and ridge regularization, we used 5-fold cross-validation in order to find the best alpha value of 0.00019 for lasso and 10 for ridge.
        For KNN, we tested multiple k-neighbors and selected the value that gave the highest cross-validated accuracy, which was 82.62% from k=1.
        For K-Means Clustering, we determined our best k-value by calculaing the WSS of various k-values within the range (1,30) and selected the value at the elbow of the plot. This would ensure the lowest complexity and lowest error and therefore, prevening overfitting. From the elbow plot, we selected a k-value of 6.
        For the NN, we used learning rate scheduler in order to test various learning rates at different stages of training. This allows us to prevent overshooting from a large learning rate and prevent slow convergence from a small learning rate. Ideally, we want to select the learning rate at which the loss is decreasing the fastest and before it starts to increase.
