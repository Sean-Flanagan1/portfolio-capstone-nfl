# Capstone Project: To Punt or Go for it on Fourth Down?

## Problem Statement

Should teams punt or go for it on fourth down?

I wanted to see if teams should punt or go for it on fourth down. One thing that bothers me when watching football is when the announcer says that the coach made a smart decision not getting caught up in the moment by punting on fourth and one. I wanted to do my own research to find out if the announcer is right. 

## Executive Summary

The goal of the project is to try and predict whether a team should go for it on fourth down or punt. I pulled an NFL Play-by-Play Data set from Kaggle. The dataset was for seasons 2009 through 2018. The dataset contained 449,371 rows and 255 features. I ran multiple classification models trying to find which model could predict most accurately which team should go for it on fourth down or not. The focus should be on accuracy because the bettor/fan would want to correctly predict the result of the play whether if it is a converted fourth down or not. Another focus on the model is precision since the coach would want to make the correct play call as a coach, maximizing the positive predictive value.

## Process

### Dropping Features

Since the NFL dataset was large, importing the data was slow and the data was difficult to read. The first step was to drop unnecessary features. I checked the features and dropped all features that contained more than 100,000 nulls. Afterwards I dropped features that would reveal the result of the play. The dataset had multiple features that included win probability added (wpa) and expected points added (epa). These features would reveal to the model if the team converted on fourth down or not so I dropped these features. I also dropped features that would have nothing do with fourth down (kick return, extra-point, two-point-attempt, etc). After dropping these features, I was able to cut down the dataset to 99 features. I was now able to start exploring the dataset and dive into finding which features are relevant when attempting to go for it on fourth down. 

### EDA

I made the target variable by creating a column for fourth down conversion. 1 if a team converts on fourth down and 0 if the team does not convert on fourth down. With this information, a team successfully converted on fourth down approximately 49% of the time. There was a total of 4,776 fourth down attempts. The next step was splitting the play type into dummy columns to see if the team ran or passed the ball, as well as the formation before the snap. I also decided to make a dummy variable for whether a team was home or not. Playing at home may or may not make it easier to convert on fourth down. I also combined field goal probability and touchdown probability into one total scoring probability to see if that would have any impact on converting on fourth down. However, before digging into creating a model, I wanted to explore expected points added (EPA) and win probability added (wpa) to see the impact of punting or going for it on fourth down.

#### EPA and WPA

It appears that teams increase their odds of winning when they attempt to go for it on fourth down compared to punting. However, some more digging needs to be done for this. EPA and WPA can be misleading. Most teams go for it in on fourth down when they are losing in the fourth quarter. Your win probability added for example is not going to drop that much that late in the game if you fail to convert when compared to punting the ball in the second quarter. 

| 4th Down Attempt | Win Probability Added | Expected Points Added |
| --- | --- | --- |
| Failed Conversion | -.0409 | -2.4424 |
| Successful Conversion | .0712 | 2.6971 |


| Punt or 4th Down Attempt | Win Probability Added | Expected Points Added |
| --- | --- | --- |
| 4th Down Attempt | .0142 | .0830 |
| Punt | -.0815 | -3.5717 |

### Models

I ran multiple classifications to try and find the model with the best accuracy and precision scores. The features I used were yards needed for a first down, whether or not the play was a run play, touchdown probability and goal to go. Features like playing on your home field and total scoring probability did not appear to have any significant correlation with converting on fourth down. 

#### Data Dictionary

| Feature | Type | Description |
| --- | --- | --- |
| 4th_down_conversion | Integer | 1 if the offense converts on fourth down. 0 if the offense fails to convert on fourth down | 
| ydstogo | Integer | Yards needed for a first down |
| run | Integer | 1 if the offense runs the ball. 0 if the offense throws the ball |
| td_prob | Float | Probability of the offense scoring a touchdown (before the fourth down attempt) |
| goal_to_go | Int | 1 if the offense is in the opponent’s goal line. 0 if the offense is not in the opponent’s goal line. |

Full list of data dictionary: https://github.com/ryurko/nflscrapR-data/tree/master/legacy_data


#### Model Results

The classification models had accuracy scores ranging from 62% to 65% and precision scores ranging from 60% to 64%. This was approximately 10% better when compared to the dummy metrics. Logistic regression had the best accuracy score at 65.66% while boosting extra trees also had accuracy scores in the 65% range. Extra trees also had the best precision score at 64.29%. Extra trees did well with both metrics. I grid searched for best parameters for all models. Extra trees had a n_estimator of 44, max_depth of six and min_sample_split of 17.

#### Accuracy and Precision Scores

| Model | Accuracy | Precision |
| --- | --- | --- |
| Logistic Regression | .6566 | .6131 |
| Boosting | .6558 | .6316 |
| Extra Trees | .6549 | .6429 |
| Random Forests | .6399 | .6047 |
| KNN | .6307 | .6083 |
| Bagging | .6281 | .6065 |
| Dummy (Most Frequent) | .5343 | N/A* |
| Dummy (Stratified) | .5293 | .495 |

\* The dummy (most frequent) model is N/A for precision because you cannot divide 0/0. This dummy model only predicted false positives and false negatives. Precision is the positive predictive value (TP/(TP+TN)).

## Conclusion
To conclude the data show that teams should go for it on fourth down given the right circumstances. While teams successfully convert on fourth down approximately 49% of the time, more research will be done to see the effect of taking out the fourth quarter (or the last few minutes of the fourth quarter) and the last 30 seconds of the second quarter. A lot of times regardless of the yardage needed for a first down, a team will go for it on fourth down because they are down by more than 3 points with a minute left. What I am more interested about is a fourth and two at the fifty-yard line when punting and going for it are both feasible options. 
 
My goal is to add a predictor that when provided with game information, it will give the probability that the team will get a first down. The question is will coaches be comfortable using a model to tell them if they should punt or go for it on fourth down. A lot of the game is stats, but there still is a gut factor and feel for how the game is going when watching. Also, lots of fans have a selective memory. Most fans will remember and criticize you if you go for it on fourth down and you fail to convert compared to remembering and praising your decision to go for it on fourth down when your team gets a first down.  

## Data Sources 
Kaggle Detailed NFL Play-by-Play Data 2009-2018: https://www.kaggle.com/maxhorowitz/nflplaybyplay2009to2016
NFL Play-by-Play Data 2009-2018 Data Dictionary: https://github.com/ryurko/nflscrapR-data/tree/master/legacy_data
