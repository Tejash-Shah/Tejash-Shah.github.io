---
title: "Embedded methods"
date: 2020-11-01
categories:
  - Feature Selection
tags: [machine learning, feature selection]
excerpt: "Machine Learning, Feature Selection"
---

**Embedded method should be done after missing values have been handled and categorical variables have been encoded.**

**1. Regularization**

Regularization consists of adding a penalty on the different parameters of the model to reduce the freedom of the model. Hence, the model will
be less likely to fit the noise of the training data and will improve the generalization abilities of the model. It's called Embedded Method because feature selection occurs at the same time model is being fit. 

**Regularization masks true relationship between features and target. Coefficients change with penalty and so it is hard to determine true association.**

 For linear models there are in general 3 types of regularization:

1. **L1 regularization/ Lasso Regression**: Will shrink some parameters to zero, therefore allowing for feature elimination.
[Link to Lasso Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Lasso.html)

2. **L2 regularization/ Ridge Regression**: As the penalization increases, the coefficients approach to zero but do not equal zero, hence no variable is ever excluded.
[Link to Ridge Regression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.Ridge.html)
3. **L1+L2 regularization/ Elastic net Regression**

As we increase the value of lambda we penalize the coefficient harder and turning the coefficient to zero. By fitting a linear or logistic regression with a Lasso regularization, we can then evaluate the coefficients of the different variables, and remove those variables which coefficients are zero.

***SUMMARY: Use Lasso Regression not Ridge Regression to do feature selection***

**2. Regression Coefficients**

Use regression coefficients to perform feature selection for linear models. We need to follow Linear model assumptions so that interpretation of regression coefficient is correct. 

1. **Linear relationship** between predictor X and target Y
2. Features are independent. 
3. **No or little multicollinearity**
4. **Multivariate-Normality**: Features are normally distributed.
5. **Homoscedasticity**: Homogeneity of variance.

In addition, for direct coefficient comparison features should be in the same scale. **Regularization highly impacts feature importance/interpretation using coefficients. For some values of regularization parameter, X1 coefficient could be higher than X2 or vice-versa.**

The magnitude of the coefficients is directly influenced by the scale of features. Therefore, to compare coefficients across features, it is important to have features with same scale. The bigger the coefficient, higher the contribution.

**3. Trees**
**Decision Tree**: For classification, measure of impurity is gain or impurity. For Regression, measure of impurity is variance. <br>
**Random Forest**:In Random Forest, the impurity decrease from one feature can be averaged over all trees to determine the final importance of the variable.

**Key Points**:

1. Correlated features show equal or similar importance
2. Correlated features importance is lower than the real importance when tree is built in absence of correlated counterparts.
3. Highly cardinal variables show greater importance (trees are biased/tend to overfit to this type of variables)

In trees, correlated features will show similar importance though smaller. If you remove the correlated feature, the remaining feature importance will also increase.

**3.1. Random Forest Importance**
**Procedure**: 

1. Build a random forest
2. Determine feature importance
3. Select the features with highest importance

**3.2. Alternative Random Forest Importance called Recursive feature elimination (RFE)**

**Procedure**: 
1. Build random forest
2. Calculate feature importance
3. Remove least important feature
4. Repeat till a condition is met. Condition could be desired number of features.

***This method is better if there are high number of correlated features to select from. Because correlated features will show similar feature importance though smaller. So, if you remove the correlated feature the remaining feature importance will increase. If we didn't do **RFE** we may remove the features that are correlated because they show smaller importance but if we do **RFE** we remove one and the importance of remaining feature increases so we will be able to keep it.***



**3.3 Gradient Boosted Trees Feature Importance**

Feature importance is calculated in the same way as Random Forest. Also, biased to highly cardinal features. Feature Importance is susceptible to correlated features.

Interpretability of feature importance is not so straightforward:
1. Later trees fit to the errors of the first trees, therefore feature importance is not necessarily proportional on the influence of the feature on the outcome, rather on the mistakes of the previous trees.

2. Averaging across trees may not add much information on true relation between feature and target
