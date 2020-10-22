# osic_kaggle
Very simple top 10 % solution for the OSIC Pulmonary Fibrosis Progression Kaggle Competition.

# Task
The task in this competition was to predict lung function decline across multiple visits for a given patient based on some basic demographics, a CT scan of his lung and the initial FVC (=forced vital capacity) value. In addition we were supposed to give confidence values for our predictions.
A more detailed description can be found on the competition website: https://www.kaggle.com/c/osic-pulmonary-fibrosis-progression

# Solution
In this repo you can find a small adaptation of my very simple final solution which is just a slightly improved version of my initial baseline model. The main points are:
1. Leak Free Cross Validation: Only using the initial FVC value as feature and also excluding not scored rows from the validation.
2. Label Encode categorial variables.
3. Normalize continuous variables.
4. A few engineered interaction features.
5. Ridge Regression with weight penalty (=alpha) of 1000.
6. Predicting delta to initial FVC values instead of absolute FVCs.
7. The formula for the confidence values I used is : 200 + 2 * t. So I would use a confidence score of 200 for predictions on the same day and a confidence score of 300 for a prediction after 50 days.

As it turns out there is not much signal in the data or at least it is hard to extract probably due to the small sample size. Anything more complex I tried, like GBMs or Quantile Regression with Neural Nets, performed much worse on cross validation and in retrospect this was confirmed by the private leaderboard where I jumped from 1000ish to ~180. place.
