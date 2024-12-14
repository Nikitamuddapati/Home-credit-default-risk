# Home-credit-default-risk

## Business Problem and Objective
Home Credit primarily uses traditional credit scoring methods to evaluate the repayment capacity of loan applicants. However, these conventional sources often misjudge clients’ repayment potential, leading to unjust credit denials or approvals for unsuitable candidates, increasing default rates and financial risk. The objective after conducting Exploratory Data Analysis is to build a model that can accurately predict which clients can pay back their loans.

## Solution

Our recommended solution is the resampled XGBoost after evaluating various models across the metrics- AUC, log loss, confusion matrix, and accuracy.

Logistic Regression(L1 - Lasso): The overall Kaggle score was 0.72820, which achieves the highest accuracy across all the models we considered. While this model only had an AUC of 0.74 for the train set and of 0.75 on the validation data, this is a very modest decline and it suggests that the model is generalizing quite well to unseen data. It’s also higher than a random classifier (Kaggle Score: 0.50) which suggests that this model is fairly decent at differentiating between the positive and negative classes.

XGBoost: This is a fairly good model with a Kaggle score of 0.72235 and an AUC of 0.75 on the validation set. This indicates that the model is generalizing well to unseen data.

Resampled XGBoost: After training on resampled data, XGBoost achieved a Kaggle score of 0.72447. Notably, the resampled XGBoost model had an AUC of 0.99 on the resampled training data and 0.98 on the validation data. This demonstrates that resampling significantly helps the XGBoost model generalize better to unseen data. The improved Kaggle score aligns with this observation, confirming that resampling improves model performance on test data as well.

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
Data Preperation, EDA, Logistic Regression Baseline Model, Class Imbalance and Non-linearity checks, Upsampling, XGboost, Tuned XGboost, Cross Validation and Grid Search, Feature Importance, Interpretations, Summaries, Final Test set and Kaggle Results

## Business Value (group)

Our solutions proves multiple benefits
•	Reduced Default Rates: Accurately predicting credit risk will allow Home Credit to minimize losses caused by loan defaults and optimize the loan approval process, minimizing risk.
•	Increased Customer Trust: by reducing rejection of creditworthy customers, long-term relationships. It also helps extend loans to a larger customer pool, including those with limited credit history.
•	Enhanced Operational Efficiency: A predictive model will help streamline decision-making processes, reducing manual intervention and lowering operational costs.


## Challenges Faced (group)

the main challenges faced was data preperation and cleaning of huge datasets and managing especially missing values and high dimensionality. Getting the models to run without errors and file knitting as it required sophisticated imputation methods and robust computational resources. Additionally, feature selection and ensuring model generalization across different data scenarios added layers of complexity to our project.

## Learnings (group)

The correlation analysis shows strong relationships between some key
variables. For instance, AMT_CREDIT and AMT_GOODS_PRICE have an almost
perfect correlation (0.99), indicating that higher loans are typically
associated with higher-value goods.


The mean annuity amount is about \$31,236 and median is
    \$29,209.5.Majority of the annuity amounts fall between \$19,548
    (25th percentile) and \$40,320 (75th percentile), while the top 10%
    exceed \$52,789.5.

-   The mean age in days is about -14,188 and median is -13,883.5.
    Majority of the ages are falling between -16,299 (25th percentile)
    and -11,664 (75th percentile) days, with the oldest 10% older than
    -18,893 days.

-   The mean of DAYS_EMPLOYED is around -2203.44, with a median of
    -1680.5. The majority of values lie between -3132.5 (25th
    percentile) and -817 (75th percentile), with the lowest 10% of
    values being below -5026.5.

-   The mean of the REGION_POPULATION_RELATIVE is about 0.0228, with a
    median of 0.0202,majority of the data falls between 0.0106 (25th
    percentile) and 0.0308 (75th percentile), with the top 10% of
    regions having population relative values above 0.0462.


vizs:  The EDA revealed interesting patterns. For example, the bar plot of
OWN_CAR_AGE vs loan default showed that clients with newer cars (0 to 10
years old) were slightly more likely to default, while those with older
cars rarely defaulted. Similarly, the histogram of DAYS_EMPLOYED
highlighted that many applicants were newly employed or had short
employment histories before applying for a loan. Those with longer
employment histories generally applied less frequently. In terms of
credit amount, applicants with higher credit amounts tended not to
default, with the median credit amount higher for non-defaulters.
Additional insights included that defaulters tended to have higher
annuity payments, with a few outliers skewing the results. The busiest
time for loan applications was between 9 AM and 12 PM, peaking around 11
AM, indicating this is when most clients submit their application.

After merging with transactional data, the dataset now has 125 columns,
with 3 additional columns and 8,579 rows, of which 8,057 clients did not
default and 522 did, maintaining the same proportion of each target
class as before. Overall, the joined data maintained similar important
features and accuracy with the pre-merged data, with only minor changes
observed in the least important variables. As a result, employment
duration, client age, and car age remain key factors in predicting loan
defaults.



    **Car Age vs Loan Default:** Majority of clients with cars
    irrespective of car age did default. A very tiny portion of clients
    with car ages between 0 to 10 years defaulted. As car age increases
    beyond 15 years, there are hardly any loan defaults meaning clients
    with old cars seem to repay more often.

-   **No.of client employed days before application:** The histogram
    shows that most people(about 2000 count) who have applied for loan
    have been employed for less than 2000 days before applying for the
    loan, with a notable peak in employment duration just around 0 days
    of employment, indicating many of them were newly employed or had a
    short employment history. Also, few of them (500 count) seem to have
    a longer employment (6000 days) before applying.

-   **Loan Default by Credit Amount:** Those who received a higher
    credit amount (in previous loan application) tend not to default(0)
    and pay back. Median credit amount is higher for default = 0
    compared to those who defaulted (1). Although both groups share
    similar ranges in respective credit amounts, with a few outliers
    present for those who failed repayment.

-   **Age vs Credit Amount by Loan Default:** The scatter plot shows the
    relationship between a client's age (in days since birth) and credit
    amount approved, filtered by default status. There is no clear
    distinction in the credit amount approved across the different ages
    between those who defaulted and did not, but a concentration of data
    points around certain ages and credit amounts is observed.

-   **Loan Default by Annuity:** Applicants who defaulted(1) tend to
    have slightly higher loan annuity amounts compared to those who did
    not (0), with a few outliers among the default group(1). The median
    annuity amount for both groups is close, though the distribution for
    defaulters appears wider.

-   **Busiest hour:** Majority of clients applied between 9 AM and 12
    PM, with a peak around 11 AM, suggesting 11 AM is the busiest hour
    for loan application processing.


Overall this was a very informative experience and we gained a lot of knowledge from the modeling process. For instance, we learned from the XGboost model that the top 5 predictors are Ext_Source_3, Ext_Source_2, Days_Birth and Amt_Annuity. This suggests that Home Credit should analyze these factors more critically when giving out loans. For instance, perhaps younger people have more difficulties with paying back loans compared to older people. This could be because they are just beginning their financial journey.

