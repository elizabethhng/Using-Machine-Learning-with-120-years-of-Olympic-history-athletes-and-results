# Using-Machine-Learning-with-120-years-of-Olympic-history-athletes-and-results
<!-- omit in toc -->
# ​Is it possible to predict whether an individual will win a medal or not  in their respective sport at the Summer Olympics ?

## Project summary
This project explores the Kaggle Dataset 20 years of Olympic history: athletes and results Source: https://www.kaggle.com/heesoo37/120-years-of-olympic-history-athletes-and-results.

The contributions of this code have been divided into three sections, 
Section A: Data Cleaning (Contributed by Goh Sheue Ling)
Section B: Data Preperation, Exploratory Analysis (Contributed by Wang Jia Rui)
Section C: Introduction, Machine Learning, Conclusion and Recomendations (Contributed by Me)

##Problem statement: Is it possible to predict whether an individual will win a medal or not in their respective sport at the Summer Olympics ?
 The overall flow was as such:
 1. Divide the data according to sports.
 2. Analyse all useful variables and identify high correlations to whether a medal was won in that event (medal_won).
 3. Shortlist the top 3 sports and possibly useful variables that can be used for prediction.
 4. Apply 4 Machine learning methods (ie. Decision Tree, Random Forest Classification, Naive Bayes Classifier, Logistic Regression)

## Result Analysis
###Goodness of Fit, Classification Accuracy, True Positive Rate(TPR) and True Negative Rate(TNR)
Since the target, Medal_Won is consistently biased towards the outcome '0' (no win) in our data, it is also easy for our machines to overfit and hence classify a huge percentage accurately as a '0'. It will cause the Goodness of Fit Accuracy to be high, however it will skew the True Positive rates to be low, and True Negative rates to be high, meaning that the models are overfitting and not doing proper prediction after all. It is important to take into account the TPR and TNR when judging the performance of our prediction models.

That being said, our models for the selected sports did not face this issue and performed generally well in this aspect. The Classification Accuracies and TNR/TPR for Baseball ranges from 0.7-0.9. For Basketball and Water Polo, the classification Accuracies and TNR are above 0.8, but the TPR ranges from 0.6-0.7 and 0.4-0.6 respectively.

There may be a stronger correlation between the variables and target, or consistency between variables and outcomes for the sport Baseball as compared to Basketball and Water Polo.

###Comparison of Machine Learning Methods
As expected, Random Forest Classification tends to do better than the Decision Tree Classfication, although minimally. This minimal difference could be due to the fact that there is not much variance or instability in the Decision Tree Model to begin with, as well as the fact that there are few features, or less deep decision trees.

For our dataset, the Naive Bayes Model did not do as well as the Decision Tree and Random Forest Models. This could be due to the fact that our data may not be perfectly Gaussian distributed, and our predictors may not be completely independent of each other, lowering the performance of the classifier.

The Logistic Regression Model's performance pales in comparison to the three other Machine Learning Methods, perhaps due to the nature of our data. Our number of samples are relatively small or imbalanced, and numerically, our variables do not have a strong enough correlation with the outcome.

In conclusion, our best results come from the sport Baseball, and the classification method Random Forest Classification. It is possible to predict whether an individual participating in the sport Baseball at the Olympics, with the attributes Team, Weight, Gender and Height.

## Conclusion and Reccomendations 
It is not easy to predict if a particular individual will win a medal at the olympics given the current dataset we worked on. Yet, we have also successfully predicted whether an individual will won a medal (Gold, Silver, Bronze) in the Baseball Olympic Event.
The Top 4 most important features in predicting if an individual will win a medal in the Baseball Olympics are:
Team/ Country Representing (Team_mean_enc)
Weight
Height
Gender (Gender_label)
We used 4 different models, in which Random Forest Classfication performed the best, followed by Decision Tree Classification, Naive Bayes Classification, and then Logistic Regression.
Still, we wish to acknowledge the limitations of our dataset and predictors, for our particular problem statement.
1. Why we have successful results, and what to note:
As shown in "Feature Importance" above, a strong feature that helped our predictions was Team_mean_enc. This Variable was encoded with the assumption that the mean value (number of times a particular country has won a medal/number of times particlar country has participated), is constant. This statistic, may show trends of which countries have a good track record and hence the assumption that the countries performance will always be of the same standard. This assumption works for prediction since it is generally true that some Teams have consistently dominated particular sports in the olympics as seen in our Exploratory Analysis, hence there is some form of relationship. Still, the variable Team is NOT the direct cause and factor as to how individuals will perform and hence whether they will win or not.

2. How can we overcome this? (Recommendations)
With our current dataset, it is limited in being able to predict one's performance in the olympics, as the current variables simply do not determine the outcome. Hence, we would like to suggest possible variables for future development.

For the particular variable Team and Team_mean_enc, instead of determining the Team's chance at winning based on statistics and assuming that the results of the predecessors will always hold true for a future participant's performance and chance at winning. Perhaps, a more accurate measure would be data and statistics that compare the resources that each Team(country) has invested in the athletes leading up to the olympics. It could be the number of Sports Academies each country has, or the resources and funding given to support the training of their olympics team.

As for individual statistics, the variables in our dataset such as Height, Weight and Gender are not the best predictors there is a wide overlapping variance across those who win a medal and do not.Furthermore, we conclude that it is a poor measure of how well an athlete will perform at the competition itself. More than just physical measurements, we suggest incorporating new data and variables that are measures of Functional Performance and Skills, directly related to the nature of the respective Olympic Sport Events. There are various professional tests statistics for the athleticism or skill of an individual such as Agility Testing, Strength Testing, Sprint Testing, Cardio Testing, Muscle Endurance etc. The combinations of Skills and Athleticism attributes are precisely what Olympians train and prepare themselves to compete against opponents in their respective sports at the olympics. Hence we believe they may have a stronger and direct correlation to whether or not they will win a medal among the rest, and it will be an interesting further development for this project.
