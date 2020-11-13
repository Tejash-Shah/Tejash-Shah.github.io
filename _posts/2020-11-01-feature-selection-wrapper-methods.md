---
title: "Feature Selection - Wrapper methods"
date: 2020-11-01
categories:
  - Feature Selection
tags: [machine learning, feature selection]
excerpt: "Machine Learning, Feature Selection"
---

**Wrapper methods/embedded methods should be applied after feature engineering to utilize the full potential of feature selection.**

***Should be performed on training set and then propagated to test set to avoid over-fitting***.

**Greedy Search algorithms**. Greedy because it evaluates all possible combinations of features and selects the subset which gives the best performance. Use a specific classifier to select the optimal set of features. They are sequential feature selection approach where they add or remove one feature at the time based on the classifier performance until a feature subset of the desired size k is reached, or any other desired criteria is met. While building model you can also perform cross validation to avoid over-fitting.

**Performance metric** could be 
1. roc_auc for classification
2. r-squared for regression

**mlextend package implements wrapper based feature selection methods** <br>

**1. Step Forward Feature Selection**

Starts from **NO** feature and add one feature at a time.

**Procedure**
1. Evaluates all subsets of 1 feature.
2. Select feature that gives the best performance.
3. Evaluates all subsets of 2 features (the first selected feature and new feature) 
4. Select feature group that gives the best performance.
5. Stop  when certain numbers of features are reached or certain performance metric is achieved.


[Link to stepforward feature selector ](http://rasbt.github.io/mlxtend/user_guide/feature_selection/SequentialFeatureSelector/) 

**2. Step Backward Feature Selection**

Starts from **ALL** features and remove one feature at a time that is least important.

**Procedure**
1. Build a model using all features.
2. Remove first feature and find the performance metric.
3. Remove that feature which gives minimum drop in performance metric. 
4. Remove second feature and find the performance metric.
5. Remove that feature which gives minimum drop in performance metric. 
6. Repeat until certain criteria is met or desired number of features is reached.

**Performance metric** could be 
1. roc_auc for classification
2. r-squared for regression

[Link to stepbackward feature selector ](http://rasbt.github.io/mlxtend/user_guide/feature_selection/SequentialFeatureSelector/) 

**3. Exhaustive Feature Selection**

Evaluate all possible combinations of one feature, all possible combinations of two features, three features and so on. Build classifiers for all possible combinations. Select feature space with highest performing algorithm. Most computationally expensive.
**For example with features size of 4, total 15 feature combinations are possible.**

1. {0}
2. {1}
3. {2}
4. {3}
5. {0, 1}
6. {0, 2}
7. {0, 3}
8. {1, 2}
9. {1, 3}
10. {2, 3}
11. {0, 1, 2}
12. {0, 1, 3}
13. {0, 2, 3}
14. {1, 2, 3}
15. {0, 1, 2, 3}

[Link to exhaustive feature selector ](http://rasbt.github.io/mlxtend/user_guide/feature_selection/ExhaustiveFeatureSelector/) 
