---
title: "Outlier Handling"
date: 2020-11-15
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
--- 

Outliers can affect the performance of linear models and adaboost.

Ways to handle outlier:

1. Trimming: Remove outliers 
2. Missing data: Treat outliers as missing data and perform missing data imputation
3. Discretisation: Put outlier in lower/upper bins
4. Censoring: Capping, Top/Bottom Encoding, Winsorization

How to detect outliers
1. **Gaussian Distribution (mean and std)**: Observations outside mean +/- 3 SD are considered outliers.
2. **Inter-quantal range proximity rule** for skewed distribution
3. **Quantiles**: Observations below 5th quantile and more than 95th quantile could be considered outliers.
4. Histogram , Boxplot, Q-Q plot
4. Tests for normality

***Note: Outliers are removed from the train set not the test set***


## Capping
### ***with IQR***
Replace outliers in either/both tails with max/min possible values found using IQR rule. 

### ***with Gaussian approximation***
cap using mean +/- 3 standard deviation rule

### ***with quantile***
cap lower values than 5 quantile to 5th quantile and values more than 95th quantile to 95th quantile

[feature engine link to perform capping using all approaches](https://feature-engine.readthedocs.io/en/latest/outliercappers/Winsorizer.html) 

## Arbitrary Capping

Cap at random minimum and maximum numbers