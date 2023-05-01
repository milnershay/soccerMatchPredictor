# soccerMatchPredictor
An ML project to predict match outcomes using four different models and comparing them
# Introduction:
The goal of this academic work is to predict soccer match outcomes using machine learning 
algorithms. The problem is formulated as a classification task, where 1 represents a home win, 0 
represents a draw, and -1 represents an away win. In this report, I will describe my approach to 
solve this problem, which involves using four different classification algorithms.
# Data:
To train and test our models, I used the dataset given, firstly we cleaned it by choosing what I
thought were the most important features for predicting match outcomes:
'season', 'date', 'home_team_api_id', 'away_team_api_id',
'home_team_goal', 'away_team_goal', 'home_player_1' , 'home_player_2',
'home_player_3', 'home_player_4', 'home_player_5', 'home_player_6', 'ho
me_player_7' ,'home_player_8' , 'home_player_9', 'home_player_10', 'hom
e_player_11', 'away_player_1', 'away_player_2', 'away_player_3', 'away_
player_4','away_player_5', 'away_player_6', 'away_player_7', 'away_play
er_8','away_player_9', 'away_player_10', 'away_player_11'
Basically looking at what players where playing for each team.
The next step was to replace the players themselves (ID) with the overall rating of each player 
and later calculating each teams average overall rating.
Then I filled all the na values with either average or most common values, and factorized 
categorical columns.
To determine the most important features, I used recursive feature elimination (RFE) technique.
## All features I had were an overall of 20 features:
'home_avg', 'away_avg', 'h_buildUpPlaySpeed', 
'h_buildUpPlayDribblingClass', 'h_buildUpPlayPassing',
'h_chanceCreationPassing', 'h_chanceCreationCrossing',
'h_chanceCreationShooting', 'h_defencePressure', 'h_defenceAggression',
'h_defenceTeamWidth', 'a_buildUpPlaySpeed',
'a_buildUpPlayDribblingClass', 'a_buildUpPlayPassing',
'a_chanceCreationPassing', 'a_chanceCreationCrossing',
'a_chanceCreationShooting', 'a_defencePressure', 'a_defenceAggression',
'a_defenceTeamWidth'
## The top 10 features I found were: 
'home_avg', 'h_buildUpPlayDribblingClass', 'h_buildUpPlayPassing','h_ch
anceCreationPassing', 'h_chanceCreationShooting','h_defencePressure', '
a_buildUpPlayDribblingClass','a_buildUpPlayPassing', 'a_chanceCreationP
assing', 'a_defencePressure'.
## The top 6 features I found were:
'h_buildUpPlayDribblingClass', 'h_buildUpPlayPassing','h_defencePressur
e', 'a_buildUpPlayDribblingClass','a_buildUpPlayPassing',
'a_defencePressure'.
# Models:
I selected four different classifiers for this task: KNN, DecisionTreeClassifier, 
RandomForestClassifier, and GradientBoostingClassifier.
K-Nearest Neighbors (KNN) is a non-parametric algorithm that uses distance metrics to classify 
instances. In KNN, the output is a classification based on the k-nearest neighbors in the training 
set.
Decision Tree is a type of classifier that uses a tree-like model of decisions and their possible 
consequences. Each internal node represents a test on an attribute, each branch represents the 
outcome of the test, and each leaf node represents a class label.
Random Forest is an ensemble learning method for classification that operates by constructing a 
multitude of decision trees at training time and outputs the class that is the mode of the classes 
(classification) or mean prediction (regression) of the individual trees.
Gradient Boosting Classifier is an ensemble learning method that produces a prediction model in 
the form of an ensemble of weak prediction models, typically decision trees.
# Testing:
I trained our models on all the seasons before 2015/2016 and tested them on that year, using all 
the features, top 10 features, and top 6 features, respectively. I used four different measures to 
evaluate the performance of our models: cross-validation score, accuracy, f-measure, and 
confusion matrix.
# Results:
Our results show that the GradientBoostingClassifier model achieved the highest average crossvalidation score and accuracy score on all features and top 10 features. However, the Random 
Forest model outperformed all other models when it came to the F-measure score. In terms of the 
confusion matrix, we can see that all models struggled to predict draws accurately, which is 
understandable considering the rarity of draws in soccer matches.
I choose those metric because accuracy is the most commonly used to see the proportion of 
correct predictions out of all predictions but it alone is not sufficient enough so I added F1 and 
confusion matrix to better see how many false positives and false negatives do I have.
I also used cross validation of the models to receive a more robust evaluation of each models 
performance since it uses multiple training and validation sets.
## Results of prediction using all 20 features:
Average cross-validation score for KNeighborsClassifier: 0.369
Accuracy score for KNeighborsClassifier: 0.418
F-measure score for KNeighborsClassifier: 0.392
Confusion matrix for KNeighborsClassifier:
 Home Draw Away
Home 475 189 348
Draw 334 189 332
ID: 314978370 Project preparation workshop
Assignment 2
Away 443 289 727
Average cross-validation score for DecisionTreeClassifier: 0.357
Accuracy score for DecisionTreeClassifier: 0.361
F-measure score for DecisionTreeClassifier: 0.345
Confusion matrix for DecisionTreeClassifier:
 Home Draw Away
Home 331 272 409
Draw 255 226 374
Away 394 420 645
Average cross-validation score for RandomForestClassifier: 0.425
Accuracy score for RandomForestClassifier: 0.454
F-measure score for RandomForestClassifier: 0.370
Confusion matrix for RandomForestClassifier:
 Home Draw Away
Home 336 81 595
Draw 181 84 590
Away 236 133 1090
Average cross-validation score for GradientBoostingClassifier: 0.447
Accuracy score for GradientBoostingClassifier: 0.476
F-measure score for GradientBoostingClassifier: 0.331
Confusion matrix for GradientBoostingClassifier:
 Home Draw Away
Home 294 11 707
Draw 184 7 664
Away 169 7 1283
## Results of prediction using top 10 features:
Average cross-validation score for KNeighborsClassifier: 0.369
Accuracy score for KNeighborsClassifier: 0.418
F-measure score for KNeighborsClassifier: 0.392
Confusion matrix for KNeighborsClassifier:
 Home Draw Away
Home 475 189 348
Draw 334 189 332
Away 443 289 727
Average cross-validation score for DecisionTreeClassifier: 0.357
Accuracy score for DecisionTreeClassifier: 0.361
F-measure score for DecisionTreeClassifier: 0.346
Confusion matrix for DecisionTreeClassifier:
 Home Draw Away
Home 318 276 418
Draw 244 243 368
Away 391 428 640
Average cross-validation score for RandomForestClassifier: 0.419
Accuracy score for RandomForestClassifier: 0.446
F-measure score for RandomForestClassifier: 0.358
Confusion matrix for RandomForestClassifier:
 Home Draw Away
Home 317 79 616
Draw 214 77 564
Away 243 126 1090
Average cross-validation score for GradientBoostingClassifier: 0.447
Accuracy score for GradientBoostingClassifier: 0.476
F-measure score for GradientBoostingClassifier: 0.331
Confusion matrix for GradientBoostingClassifier:
 Home Draw Away
Home 294 11 707
Draw 184 7 664
Away 169 7 1283
## Results of prediction using top 6 features:
Average cross-validation score for KNeighborsClassifier: 0.369
Accuracy score for KNeighborsClassifier: 0.418
F-measure score for KNeighborsClassifier: 0.392
Confusion matrix for KNeighborsClassifier:
 Home Draw Away
Home 475 189 348
Draw 334 189 332
Away 443 289 727
Average cross-validation score for DecisionTreeClassifier: 0.354
Accuracy score for DecisionTreeClassifier: 0.359
F-measure score for DecisionTreeClassifier: 0.339
Confusion matrix for DecisionTreeClassifier:
 Home Draw Away
Home 312 287 413
Draw 259 216 380
Away 388 405 666
Average cross-validation score for RandomForestClassifier: 0.422
Accuracy score for RandomForestClassifier: 0.457
F-measure score for RandomForestClassifier: 0.370
Confusion matrix for RandomForestClassifier:
 Home Draw Away
Home 335 84 593
Draw 197 79 579
Away 209 144 1106
Average cross-validation score for GradientBoostingClassifier: 0.447
Accuracy score for GradientBoostingClassifier: 0.476
F-measure score for GradientBoostingClassifier: 0.331
Confusion matrix for GradientBoostingClassifier:
 Home Draw Away
Home 294 11 707
Draw 184 7 664
Away 169 7 1283
# Conclusions:
My conclusions, are that I found that the GradientBoostingClassifier model achieved the highest 
performance on average. However, each model has its own strengths and weaknesses, and the 
best choice may depend on the specific problem at hand.
I should also note that the rarity of draws in soccer matches makes the task of predicting them a 
challenging one.
Overall it seems that all 4 models gave similar results and not very high predictions rate, being 
accurate around only 50% of the time
