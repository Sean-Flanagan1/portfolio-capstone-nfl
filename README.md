# Capstone Project

## Problem Statement

Should teams punt or go for it on fourth down?

I wanted to see if teams should punt or go for it on fourth down. One that bothers me when watching sports is when the announcer says that the coach made a smart decision not getting caught up in the moment when they punt the ball when it is a fourth and one. I wanted to do my own research to find out if the announcer is right. 

## Executive Summary

The goal of the project is to try and predict whether a team should go for it on fourth down or punt. I pulled a NFL Play-by-Play Data set from Kaggle. The dataset was for seasons 2009 through 2018. The dataset contained 449,371 rows and 255 features. I ran multiple classification models trying to find which model could predict most accurately which team should go for it on fourth down or not. The focus should be on accuracy because the coach would want to correctly predict the result of the play whether if it ia a converted fourth down or not. 

## Process

### Dropping Features

Since the NFL dataset was large, importing the data was slow and the data was difficult to read. The first step was to drop unnecessary features. I checked the features and dropped all features that contained more than 100,000 nulls. Afterwards I dropped features that would reveal the result of the play. The dataset had multiple features that included win probability added (wpa) and expected points added (epa). These features would reveal to the model if the team converted on fourth down or not so I dropped these features. I also dropped features that would have nothing do with fourth down (kick return, extra-point, two-point-attempt, etc.)

### EDA

After dropping these features, I was able to cut down the dataset to 99 features. I was now able to start exploring the dataset and start to explore the data.

### 

| 4th Down Attempt | Win Probability Added | Expected Points Added |
| --- | --- | --- |
| Failed Conversion | -.0409 | -2.4424 |
| Successful Conversion | .0712 | 2.6971 |


| Punt or 4th Down Attempt | Win Probability Added | Expected Points Added |
| 4th Down Attempt | .0142 | .0830 |
| Punt | -.0815 | -3.5717 |


### Data Dictionary

| Feature | Type | Description |
| --- | --- | --- |
| 4th_down_conversion | Integer | 1 if the offense converts on fourth down. 0 if the offense fails to convert on fourth down |
| ydstogo | Integer | Yards needed for a first down |
| run | Integer | 1 if the offense runs the ball.  0 if the offense throws the ball |
| td_prob | Float | Probability of the offense scoring a touchdown (before the fourth down attempt) |
| goal_to_go | Int | 1 if the offense is in the opponents goal line. 0 if the offense is not in the oppents goal line. |

Full list of data dictionary: https://github.com/ryurko/nflscrapR-data/tree/master/legacy_data

### Models

Optimizing for accuracy:

| Model | Accuracy Score |
| --- | --- |
| Logistic Regression | .6566 |
| Boosting | .6558 | 
| Extra Trees | .6541 |
| Random Forests | .6516 |
| KNN | .6307 |
| Bagging | .6147 |
| Dummy (Most Frequent) | .5343 |
| Dummy (Stratified) | .5293 |


## Conclusion

## Data Sources
Kaggle Detailed NFL Play-by-Play Data 2009-2018: https://www.kaggle.com/maxhorowitz/nflplaybyplay2009to2016
NFL Play-by-Play Data 2009-2018 Data Dictionary: https://github.com/ryurko/nflscrapR-data/tree/master/legacy_data
