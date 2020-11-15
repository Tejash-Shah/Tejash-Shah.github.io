---
title: "Feature Engineering - Discretisation"
date: 2020-11-14
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
---

Also called binning, where we transform continuous variable into discrete variable by creating a set of bins or intervals of values or contiguous intervals. Can improve the  spread of the variable. Can also handle outlier, as they will be placed in lower or upper interval at the end of the distribution.

 | Unsupervised | Supervised | 
| :---:         |     :---:      |     
| Equal-Width   | Decision Tree    | 
| Equal-Frequency(Quantile)      |       | 
| K-Means          |      | 


**Supervised techniques** are governed by the target we want to predict

## 1. Equal-Width Discretisation

Divides continuous feature into N bins of same width. Does not improve the value spread of the feature. Category encoding can be applied after discretisation.

```Width = (max_value-min_value)/N; # N=width```

[EqualWidthDiscretiser from feature engine](https://feature-engine.readthedocs.io/en/latest/discretisers/EqualFrequencyDiscretiser.html)

## 2. Equal-Frequency Discretisation

Divides the continuous feature into bins having same number of observations. Distribution of values is more homogenous than equal width discretisation i.e. improves values spread.

[EqualFrequencyDiscretiser from feature engine](https://feature-engine.readthedocs.io/en/latest/discretisers/EqualFrequencyDiscretiser.html#equalfrequencydiscretiser)


## 3. K-Means Discretisation

Use K-means clustering to find the bins from the continuous variable. Does not improve value spread. Handle outliers although outlier may impact clusters.

### ***Note: To improve the performance of linear models, ordinal encoding after Equal Frequency encoding can be applied to introduce monotonic relationship between the feature and the target***

## 4. Discretisation with Decision Tree

Use decision tree to find the optimal bins. Leaf node probabilities can be used to create bins.

**Advantage**: Creates a monotonic relationship between feature and target. Does not improve variable spread. Handle outliers as tree based model(DT) are robust to outliers. If you don't observe a monotonic relationship in test set probably you overfit on train data. In order to obtain monotonic relationship for both datasets, train and test perform hyperparameter tuning.


[DecisionTreeDiscretiser from feature engine](https://feature-engine.readthedocs.io/en/latest/discretisers/DecisionTreeDiscretiser.html): Automatically find the best tree to bin a variable.

[Article on towardsdatascience](https://towardsdatascience.com/discretisation-using-decision-trees-21910483fa4b)


## 5. Domain Knowledge Discretisation

This type of discretisation could be useful when there are requirements from outside of machine learning model to create specific bins. We define ```buckets, ex: [1,2,3,4,5]``` and ```labels, ex:[a,b,c,d,e]``` and we can use ```pd.cut()``` to create bins

