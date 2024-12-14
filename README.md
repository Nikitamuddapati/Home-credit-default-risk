# Home-credit-default-risk

## Business Problem and Objective
Home Credit primarily uses traditional credit scoring methods to evaluate the repayment capacity of loan applicants. However, these conventional sources often misjudge clients’ repayment potential, leading to unjust credit denials or approvals for unsuitable candidates, increasing default rates and financial risk. The objective after conducting Exploratory Data Analysis is to build a model that can accurately predict which clients can pay back their loans.

## Solution
xgboost
all models, kaggle scores and auc scores

Logistic Regression(L1 - Lasso): The overall Kaggle score was 0.72820, which achieves the highest accuracy across all the models we considered. While this model only had an AUC of 0.74 for the train set and of 0.75 on the validation data, this is a very modest decline and it suggests that the model is generalizing quite well to unseen data. It’s also higher than a random classifier (Kaggle Score: 0.50) which suggests that this model is fairly decent at differentiating between the positive and negative classes.

XGBoost: This is a fairly good model with a Kaggle score of 0.72235 and an AUC of 0.75 on the validation set. This indicates that the model is generalizing well to unseen data.

Resampled XGBoost: After training on resampled data, XGBoost achieved a Kaggle score of 0.72447. Notably, the resampled XGBoost model had an AUC of 0.99 on the resampled training data and 0.98 on the validation data. This demonstrates that resampling significantly helps the XGBoost model generalize better to unseen data. The improved Kaggle score aligns with this observation, confirming that resampling improves model performance on test data as well.

Remaining Models

Random Forest: 0.68575

Random Forest (Resampled): 0.67885

Logistic Regression: 0.62108

Naive Bayes: 0.60178

Decision Tree Resampled: 0.53726

Decision Tree: 0.52951

KNN: 0.52637

MLP: 0.50022

Overall this was a very informative experience and we gained a lot of knowledge from the modeling process. For instance, we learned from the XGboost model that the top 5 predictors are Ext_Source_3, Ext_Source_2, Days_Birth and Amt_Annuity. This suggests that Home Credit should analyze these factors more critically when giving out loans. For instance, perhaps younger people have more difficulties with paying back loans compared to older people. This could be because they are just beginning their financial journey.

## Contribution
Data Preperation, EDA, Logistic regression baseline model, class imbalance and non-linearity, Upsampling, XGboost, Tuned XGboost, Feature Importance, Interpretations, Summaries, Final Test set and Kaggle Results

## Business Value (group)


## Challenges Faced (group)


## Learnings (group)
