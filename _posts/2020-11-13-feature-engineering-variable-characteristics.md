---
title: "Feature Engineering - Variable Characteristics"
date: 2020-11-13
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
---


1. Missing data
2. Cardinality
3. Linear Model assumptions
4. Variable Distribution
5. Presence of Outlier
6. Feature Magnitude

## 1. Missing data
When there is no value recorded for a feature in the data. Causes: Lost, does not exist, not found, user does not want to provide info. May distort the variable distribution. Incompatible with scikit-learn. Each data point has some probability of missing. Process that governs these probabilities is called ***missing data mechanism*** or ***response mechanism*** 

[Notes](https://stefvanbuuren.name/fimd/sec-MCAR.html)
### Three mechanism that lead to missing data: 
1. **MCAR**: ***Missing completely at random***. If the probability of being missing is the same for all the observations, then the data are said to be missing completely at random (MCAR). Example is when we take a random sample of a population, where each member has the same chance of being included in the sample. The (unobserved) data of members in the population that were not included in the sample are MCAR. MCAR is often unrealistic for the data at hand.

2. **MAR**: ***Missing at random***. If the probability of being missing is the same only within groups defined by the observed data, then the data are missing at random (MAR). The probability of missing data depends on available information. Example of MAR is when we take a sample from a population, where the probability to be included depends on some known property. MAR is more general and more realistic than MCAR. Modern missing data methods generally start from the MAR assumption.
3. **MNAR**:  ***Missing not at random***. If neither MCAR nor MAR holds, then we speak of missing not at random (MNAR). In the literature one can also find the term ***NMAR (not missing at random)*** for the same concept. MNAR means we know why missing values are introduced in the dataset.

Get familiar with data collection process to understand the mechanism for missing data and then use the appropriate imputation technique 

## 2. Cardinality

The number of different labels in a feature is known as cardinality.
1. If labels only appear in train set then model will overfit to training data
2. If labels only appear in test set then model will not know to make used of unseen labels and will cause operational problems

Variables with too many labels tend to dominate other features with fewer labels, especially in tree based algorithms. ***Reducing cardinality may improve the performance.***

## 3. Rare Labels

Labels which appear in tiny proportion in a feature. ***Rare Label has the same effect has high cardinality***


## 4. Linear Model Assumptions
Linear Models = Linear, Logistic Regression, LDA, PCR
1. **Linear relationship between features and target**.  
Check:
    1. scatter plot
Fix:
    2. Try non-linear transformations of features/target to improve linear relationship.

2. Multivariate normality: Variable follow a Gaussian distribution. Check ***Histogram and Q-Q plots*** or statistically test using ***Kolomogorov-Smirnov test***. Try non-linear (logarithmic transformation) to fix this issue.

3. No or little co-linearity. Multicollinearlity occurs when features are correlated with each other. Can be checked with correlation matrix or Variance Inflation Factor **(VIF)**

4. Homoscedasticity (Homogeneity of variance): Residual has constant variance across all independent variables. Check using: <br>
    1. Residuals plot: If the relationship between X and y is linear, residuals should be normally distributed centered around 0
    2. Levene's Test
    3. Barlett's Test 
    4. Goldfeld-Quandt Test

    Non-linear transformations and feature scaling can improve homoscedasticity


## 5. Variable distribution

Probability distribution is a function that describes the probability each value can take.

Probability distribution: 

1. Discrete <br> 
    1.1. Binomial <br> 
    1.2. Poisson <br> 
2. Continuous <br> 
    2.1. Gaussian  <br> 
    2.2. Skewed: Left skewed distribution(A "skewed left" distribution is one in which the tail is on the left side) is called negatively-skewed distribution, right-skewed is called positive-skewed distribution
    2.3. Others <br> 

## 6. Outlier

Outlier is a point/observation which is distant from other points. Better to quantify the "distant" when determining outliers. Linear models and Adaboost are affected by outliers. Tree based models are robust to outliers.

For normal distribution, 3 SD away from mean are considered to be outliers. 

For skewed distribution, use IQR formula

[link](https://pro.arcgis.com/en/pro-app/help/analysis/geoprocessing/charts/box-plot.htm) to boxplot

## 7. Feature Magnitude

Regression coefficient is directly affected by the scale of variable. Features with bigger range of values tend to dominate over features with small magnitude. Feature scaling helps to in SVM by reducing the time find support vectors. 

**Models affected** by magnitude of features:

1. Linear and Logistic Regression
2. Support Vector Machine 
3. Linear Discriminant Analysis
4. Principal Component Analysis
5. Neural Networks
6. K nearest Neighbor
7. K means clustering

**Models not affected** by magnitude of features:

1. CART (Classification and Regression Tree)
2. Random Forests 
3. Gradient Boosted Trees


