---
title: "Filter methods"
date: 2020-11-01
categories:
  - Feature Selection
tags: [machine learning, feature selection]
excerpt: "Machine Learning, Feature Selection"
---

 **1. Basic Methods**

 * **Constant features**: Only one unique in feature.
 * **Quasi-Constant features**: One value in a feature has count of 99% or more. Same value for majority of observations.
 * **Duplicated Features**:  Two or more features that have almost same feature values.


**2. Correlation**

 Association between two variables with strength. Predictors should be correlated to the target but not with themselves. Correlated features does not affect model accuracy per se. ***Correlation affects model interpretability particularly linear models.*** Different algorithms show different sensitivity to correlated features. Linear models are sensitive to correlated features but tree based models are robust to correlated features.

 * Pearson Correlation coefficient: Value lies between -1 to 1.

**3. Statistical and Ranking Methods**:
 1. Mutual Information Gain
 2. Fisher Score
 3. Univariate Tests
 4. Univariate roc-auc/rmse

**Two steps**: 
 1. Rank features based on certain criteria/ metric. 
 2. Select features with high ranking.

**Pros**:
 1. Fast
 2. Doesn't care about feature redundancy or feature with low ranking combine with other feature can give rich information.  

**3.1 Mutual Information**

 Tells about the mutual dependence of two variables. If two variables are independent mutual information is zero. **Only works with numerical variables. Can be used for both Classification and Regression**
 
 1. How much of one variable can be explained using another variable. 
 2. How much information does two variable X and Y share.


**3.2 Fisher Score**
 Measures the dependence of 2 variables. Used for **categorical variables** and **binary classification**. Variable values should have non-negative, Boolean, frequencies, or counts values. We compute the chi-square values for each non-negative feature and class. Lower the p-value, the most predictive is the feature but it is not necessary that lowest p-value will be highly significant feature; lowest p-value could be because of large sample size.


**3.3 Univarate Statistical Tests**
It measures the dependence of 2 variables. Select features based on univariate statistical test like **ANOVA. Used for continuous features in classification and regression. Sensitive to the sample size**. Compares the distribution of variable when target is zero and distribution of variable when target is one. Calculate the F-Score.

Assumptions
* Assumes linear relationship between variable and target
* Assumes variables are normally distributed

If the assumptions are violated then p-values obtained from this assumptions are not valid/trustable.

***Features with p-value.0.05 are not tend to be important. If you find feature with p-value>0.05 it is not necessary that feature is not important, it might happen that feature does not have linear relationship with target as test assumption says.***


**3.4 Univariate ROC-AUC / RMSE**

Use machine learning model to predict target with every single feature. Suited for all types of variables and does not makes any assumption about the distribution of the variables

Does not consider feature interaction/redundant feature. Therefore may end up with redundant feature space.

Procedure
1. Builds machine learning model(decision tree) using a single variable and the target
2. Ranks the features according to roc-auc(Classification) or rmse(Regression)
3. Selects the features with highest performance metric.


**A good screening method to do QUICK feature selection**

***Remove features with roc-auc = 0.5 (no better than random), again the 0.5 is subjective and subject to change. Cut-off for RMSE is depended on the problem you are trying to solve.***

***Higher the roc-auc better the feature and lower the MSE better the feature***

