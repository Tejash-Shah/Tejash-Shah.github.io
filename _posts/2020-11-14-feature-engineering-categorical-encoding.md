---
title: "Feature Engineering - Categorical encoding"
date: 2020-11-14
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
---

Categorical encoding is a technique replacing the category strings by a numerical representation. 

1. Traditional Techniques <br>
    1.1. One Hot Encoding <br>
    1.2. Ordinal/Label Encoding <br>
    1.3. Count/Frequency Encoding  <br>

2. Monotonic Relationship  <br>
    2.1. Ordered Label Encoding  <br>
    2.2. Mean Encoding  <br>
    2.3. Probability Ratio Encoding <br>
    2.4. Weight of Evidence  <br>

3. Alternative techniques  <br>
    3.1. Binary Encoding  <br>
    3.2. Feature Hashing  <br>
    3.3. Others  <br>

Advantages of Monotonic relationship <br>
1. Improve the performance of linear models
2. May improve the performance of tree based models. Creates shallower trees.

## Encoding Techniques: Rare Labels
1. One Hot Encoding of Frequent Categories
2. Grouping of Rare Categories

# **Traditional Techniques**
# 1. One Hot Encoding
This technique consists of creating creating a unique column for each of the category in the feature, thus creating columns equal to cardinality. Each column is marked 1 or 0 depending on the particular observation.

## One hot encoding into k -1 variables
More generally, a categorical variable should be encoded by creating k-1 binary variables, where k is the number of distinct categories. Therefore, encoding categorical variables into k - 1 binary variables, is better, as it avoids introducing redundant information.

**There are situations when it's better to encode variables into k dummy variables**:
1. When building tree based algorithms because while building tree, tree doesn't take all features
2. When doing feature selection by recursive algorithms
3. When interested in finding the feature importance

## Advantages
1. No assumption about the distribution or categories of the categorical variable
2. Keeps all the information of the categorical variable
3. Suitable for linear models

## Limitations
1. Expands the feature space and may introduce redundancy
2. Does not add extra information

# 2. One hot encoding of top categories
Perform one hot encoding only for the most frequent categories in a feature. In the winning solution of the KDD 2009 cup, the authors limit one hot encoding to the 10 most frequent labels of the variable.

## Limitations
Lose the information regarding rare labels

# 3. Label / Ordinal / Integer encoding
Consists of replacing the categories with integer. Integer ranges from 0 to n-1 where n is total number of categories in a feature.

## Advantages
Can work well enough with tree based algorithms

## Limitations
1. Not suitable for linear models
2. Does not handle new categories in test set automatically

# 4. Count or frequency encoding
This technique involves replacing category with counts or frequency.

## Advantages
Can work well enough with tree based algorithms

## Limitation
If two category have same number of appearance in the data, they will be replaced by same number thus losing information

# **Monotonic Relationship**
Creates monotonic relationship between categorical variable and target
# 1. Ordered Ordinal Encoding
Categories are replaced by integers from 1 to k, where k is the number of distinct categories in the variable, but this numbering is obtained by the mean of the target for each category
## Limitations
1. May lead to overfitting

# 2. Mean or target encoding
This technique includes replacing the category in the categorical variable with the average of target
## Limitations
1. May lead to overfitting
2. If two categories have same mean of the target, they will be replaced by same value and possibly loss of information.

# 3. K-Fold Target Encoding

## Limitations
1. May lead to overfitting

# 4. Probability Ratio Encoding

# 5. Weight of Evidence Encoding






