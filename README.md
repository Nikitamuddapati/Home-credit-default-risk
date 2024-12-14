# Home-Credit-Default-Risk

## Business Problem and Objective

Home Credit primarily uses traditional credit scoring methods to evaluate the repayment capacity of loan applicants. However, these conventional sources often misjudge clients’ repayment potential, leading to unjust credit denials or approvals for unsuitable candidates, increasing default rates and financial risk. The objective after conducting Exploratory Data Analysis is to build a model that can accurately predict which clients can pay back their loans.

## Solution

**Final Project:** [Download the PDF version](https://colab.research.google.com/drive/1QH8d6sJC3xr_IYy3aS4_d2IKYRhsregj?usp=drive_open)
**Modelling:** https://nikitamuddapati.github.io/Home-credit-default-risk/modelling_nikita.html

The recommended solution for this project is the resampled XGBoost after evaluating various models across various metrics- AUC, log loss, confusion matrix, and accuracy.

**Logistic Regression(L1 - Lasso):** The overall Kaggle score was 0.72820, which achieves the highest accuracy across all the models considered. While this model only had an AUC of 0.74 for the train set and of 0.75 on the validation data, this is a very modest decline and it suggests that the model is generalizing quite well to unseen data. It’s also higher than a random classifier (Kaggle Score: 0.50) which suggests that this model is fairly decent at differentiating between the positive and negative classes.

**XGBoost:** This is a fairly good model with a Kaggle score of 0.72235 and an AUC of 0.75 on the validation set. This indicates that the model is generalizing well to unseen data.

**Resampled XGBoost:** After training on resampled data, XGBoost achieved a Kaggle score of 0.72447. Notably, the resampled XGBoost model had an AUC of 0.99 on the resampled training data and 0.98 on the validation data. This demonstrates that resampling significantly helps the XGBoost model generalize better to unseen data. The improved Kaggle score aligns with this observation, confirming that resampling improves model performance on test data as well.

Remaining Models Kaggle Scores:

Random Forest: 0.68575

Random Forest (Resampled): 0.67885

Logistic Regression: 0.62108

Naive Bayes: 0.60178

Decision Tree Resampled: 0.53726

Decision Tree: 0.52951

KNN: 0.52637

MLP: 0.50022


## Contribution

**Data Preparation and EDA:** 
-	Managed the initial stages of dataset, handling missing values, outliers, and variable scaling. 
-	Conducted in-depth exploratory data analysis to uncover patterns and correlations which informed feature selection and preprocessing strategies.

**Upsampling:**
-	Addressed class imbalance using upsampling to enhance representation of minority class, ensuring reduced bias in model predictions. 
-	Addressed non-linearity in relationships to improve model robustness.

**Modelling:**  
-	Built a baseline logistic regression model to establish a reference point for performance. 
-	Evaluated the influence of key predictors from penalized Lasso and made log-odds-to-probabilities conversions for interpretability.
-	Developed an initial XGBoost and resampled XGBoost model to improve accuracy and performance.

**Cross-Validation and Grid Search:**
-	Implemented cross-validation and grid search to systematically evaluate the model across multiple hyperparameter configurations.

**Feature Importance:**
-	Analyzed feature importance from the model to identify the most significant predictors, providing actionable insights for data-driven decision-making.

**Interpretations:**
-	Interpreted and summarized results and findings, visualized outcomes, and provided clear explanations to make the findings comprehensible and actionable for 
  stakeholders.

**Final Test Set and Kaggle Results:** 
-	Evaluated the final model on the test set, submitted predictions to Kaggle, and analysed the leaderboard results to validate model performance.


## Business Value

**Reduced Financial Risk:** Accurate predictions will allow Home Credit to minimize loan default losses and optimize the loan approval process. I chose to evaluate the median loss instead of the average as it is a more robust measure when data is skewed. 

*Initial loss*:

•	**Median Loss from Default (Defaulters): $24,412**

•	**Median Loss from Incorrect Rejection (Non-Defaulters): $23,800**

*Reduction in loss after model deployment*:

•	**Median Reduced Loss for Defaulters: $22,308.51 per customer**

•	**Median Reduced Loss for Non-Defaulters: $23,757.16 per customer**

•	**Total Reduced Loss: $329,692,235.11**


**Enhanced Operational Efficiency:** Helps automate processes by saving time and resources spent manually on assessing loan applications.

**Increased Customer Trust:** With better risk management, Home Credit can confidently build trust and foster long-term relationships. It also helps extend loans to a larger customer pool, including those with limited credit history.


## Challenges 

I faced several challenges, starting with cleaning large datasets, particularly dealing with missing values and high dimensionality. I worked diligently to implement sophisticated imputation methods and built various algorithms to remove unnecessary variables. Particularly the XGBoost would take days to run and required robust computational resources for smooth execution. Hyperparameter tuning, feature selection and ensuring generalizability across the training and validation datasets added complexity to the project. Additionally, file knitting was quite time-taking that required precision and attention to detail. 

## Learnings 

**Business Understanding:**

Some key learnings that I gained from my analysis include identifying strong relationships between key variables, such as the near-perfect correlation (0.99) between AMT_CREDIT and AMT_GOODS_PRICE, which means that higher loans are tied to higher-value goods. The EDA revealed interesting patterns- for example, newer car owners being slightly more likely to default, while older car owners rarely default. 

The mean annuity amount stands at $31,236. Additionally, applicants with longer employment histories applied less frequently, and higher credit amounts correlated with lower default rates. Moreover, most loan applications occurred between 9 AM and 12 PM, peaking at 11 AM. Insights from merged transactional data also confirmed these trends with minimal deviations.

I learned from the XGBoost model that the top factors influencing default are external sources, client age and loan annuity amount. Perhaps younger people have more difficulties with paying back loans compared to older people. This could be because they are just beginning their financial journey. Home Credit should analyse these factors more critically while giving out loans. 

**Analytical Learnings:**

•  Enhanced my understanding of ensemble methods and gradient boosting.

•	 Improved my skills in preprocessing and feature engineering for complex datasets.

•	 Strengthened my ability to translate technical insights into actionable business strategies.


Overall, it was a very informative experience and I gained a lot of knowledge from this project.





