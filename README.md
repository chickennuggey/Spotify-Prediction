# Spotify Prediction Final Project
By: Cynthia Nguyen, Srishti Ganu, Magge Wang, Shawn Mosharaf, Briana Nguyen

### Main Report

#### I. Dataset 
The dataset our team used was the **Spotify Tracks Dataset**: maharshipandya/spotify-tracks-dataset

#### II. Goal 
The problem our team decided to address was predicting **energy** based on acousticness, loudness, instrumentalness, and other factors. We focused on features that most correlated with energy to analyze the relationships between the features and predict energy value based on these relationships between features. 

#### III. Key Methodology
In order to address this problem, we chose logistic regression as our key methodlogy because we wanted to identify if the energy level is categorized as low or high based on a variety of variables.  Doing logistic regression allows us to catgorized songs based on their prediction score, and adjusting the threshold to fit what we would want to classify as high or low energy songs.  Therefore if we prefer would want to see more songs categorized as high level, we would move the threshold to that preference of classification.  Logistic regression allows for a simple, fast and efficient model to classify high and low energy songs.

#### IV.  Results
We were able to get a prediction accuracy of 82.60%, as in a prediction error of 17.40%.  We created a confusion matrix, which had a true positive rate of 0.7871, and a true negative rate of 0.8652, where positive corresponds to high energy level, and negative corresponds to low energy level.  We also had a ROC curve with an AUC of 0.91, revealing our model performed well in distinguishing between the classes, but may sometimes classify a lower energy song as high energy (false positives).  We did cross validation with 5 folds, and had an average cross validation accuracry of 82.10%.  Overall, this method was able to perform well in classifying the two energy levels given the input parameters.  This model has limitations that it does not account for the complex relationships between variables, however when comparing with the neural network model, the prediction the accuracy is 82.70%, which is very similar to our logistic regression model.  Thus the logistic regression model is similarly accurate to the neural network model while being more simple and computationaly fast.

#### V. Code Usage
To use the code from our project on the dataset, you can run this python notebook to see our analyses, plots, and results for our applications of linear regression, logistic regression, KNN, K-means clustering, and a neural network. The last module can be used to predict energy level for new spotify track data samples. All additional code and data can be found in our github repository (https://github.com/Srishtiganu/m148_group/tree/main), which includes the following files:
  * APPENDIX.md: Discussion on the methods applied in our project
  * main.ipynb: Finalized code for the project
  * appendix.ipynb: Additional code that was not tailored towards the final goal of the project
  * CSM148_Group_Project.ipynb: Collective code from our project check-ins
  * csv folder: Folder containing additional datasets we have used in our project check-ins
