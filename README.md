# Capstone Project

## Problem Statement

Should teams punt or go for it on fourth down?

I wanted to see if teams should punt or go for it on fourth down. One that bothers me when watching sports is when the announcer says that the coach made a smart decision not getting caught up in the moment when they punt the ball when it is a fourth and one. I wanted to do my own research to find out if the announcer is right. 

## Executive Summary

The goal of the project is to try and predict whether a team should go for it on fourth down or punt. I pulled a NFL Play-by-Play Data set from Kaggle. The dataset was for seasons 2009 through 2018. The dataset contained 449,371 rows and 255 features. I ran multiple classification models trying to find which model could predict most accurately which team should go for it on fourth down or not. The focus should be on accuracy because the coach would want to correctly predict the result of the play whether if it ia a converted fourth down or not. 

## Process

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
# capstone-nfl
# capstone-nfl
# capstone-nfl
# capstone-nfl
# capstone-nfl-data
# capstone-nfl-data
# capstone-nfl-4th-down
# portfolio-capstone-nfl
