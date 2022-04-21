# Report: Predict Bike Sharing Demand with AutoGluon Solution
This project is developed as coursework for Udacity Nanodegree. As an objective is to build a model to predict daily bike rental ridership by using of Autogluon library.
## Initial Training
### What did you realize when you tried to submit your predictions? What changes were needed to the output of the predictor to submit your results?
During a few submissions model performance was improved, score have been less after doing following actions in feature engineering. Also its was required to check output of the predictor, whether there is no negative values in predictions, in that case to set them to zero.

### What was the top ranked model that performed?
Best score of model performance was reached in new hpo weighted ensemble 0.45708.

## Exploratory data analysis and feature creation
### What did the exploratory analysis find and how did you add additional features?
In EDA I have explored data by vizualization of some plots, like heat map where have been discovered  high correlation in input variables('season' and 'month', 'temp' and 'atemp'), decribe function of dataframe in pandas shows statistics for each feature such as min, max and procentile of frequence variables and histogram plots give bars where its seen for example when (more at working days than holidays) and in what weather was more often is used rent. Another influence for performance was made  adding more features by considering whether part of day('hour) and weather conditions('atemp', 'humidity', 'windspeed') are comfortable, for example: division of ' humidity' to 'very humid', 'mild humid' and 'not humid', changing of type some int inputs to category or boolean. New features were added by splitting 'datetime': 'day', 'month', 'year', 'hour'.
### How much better did your model preform after adding additional features and why do you think that is?
Initial score(1.79572) before adding additional features score was improved to 0.78285. Importance of features is shown below, bigger impact on mdel brings time features: part day, hour, working day
![image](https://user-images.githubusercontent.com/44052996/164420296-5c2990ce-abeb-4f67-bffa-7d08be59dfd6.png)


## Hyper parameter tuning
### How much better did your model preform after trying different hyper parameters?
There are a lot of capabilites for implementation of hpo in autogluon library, as recommended in documentation and official page of developers by using of as attribute preset 'best_quality' in fit function of predictor it selects best models for creation weighted ensemble,also during tuning of hpo I have tried another capabilities  such as enabling of attribute auto_stack=True in predictor.fit, which makes automatical stacking and bagging in ensemble, and also predictor.distill, function distill produce more accurate model than the same model in fit.

### If you were given more time with this dataset, where do you think you would spend more time?
I guess for getting better model performance its needed more time for feature engineering.

### Create a table with the models you ran, the hyperparameters modified, and the kaggle score.


|model|Training Data|Time Limit|Architecture of model|score|
|--|--|--|--|--|
|initial|Standard Features & Non-Category|600| default attributes |1.79572|
|add_features|Hours, Days & Months added with Change type to category |600| add preset 'best_quality'|0.78285|
|hpo|Hours, Days & Months added with Change type to category	|600| default hpo space|0.45708|


### Create a line plot showing the top kaggle score for the three (or more) prediction submissions during the project.

![image](https://user-images.githubusercontent.com/44052996/164391330-483a231b-3262-43b5-918b-b2030833ae1a.png)


## Summary
I have got knowledge from this project. I was familiar with AutoGluon before, just without using  SageMaker in AWS. It was interestingto try it for usecase and to compare own results of score  in competition on leaderboard. Investigation of capabilites of this autoML technique was useful experience. Better model performance can be reached by tuning the hyperparameters and experiments with attributes or functions. Before training a variety of models its required make EDA and Feature Engineering. The score is not so accurate of course can be improved  the performance of the models and reach a good position on Leaderboards!
