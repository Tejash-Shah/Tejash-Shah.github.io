---
title: "Feature Engineering - Feature Scaling"
date: 2020-11-15
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
--- 

Feature scaling refers to normalize the features in the dataset. It is the last step in the modeling part and performed right before training machine learning model

Regression coefficient is directly affected by the scale of variable. Features with bigger range of values tend to dominate over features with small magnitude. Feature scaling helps SVM by reducing the time to find support vectors. 

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

## Scaling methods

1. **Standardization**
2. Mean normalization
3. **Scaling to maximum and minimum** - MinMaxScaling
4. Scaling to absolute maximum - MaxAbsScaling
5. Scaling to median and quantiles - Robust scaling
6. Scaling to unit norm

***Bolds are popular methods***


### **1. Standardization**: 
Find z-score (```z-score=(X-X_mean)/X_std```) and replace the value with z-score. 

Centres the variable at 0 and set the variance to 1. Preserves the shape of original distribution and also preserves outliers.


### **2. Mean Normalization**: 
Replace values with ```(X-X_mean)/(X_max-X_min)```. Numerator centers the variable to 0 and denominator rescales the value to variable range. Variance varies, may change the original distribution and minimum and  maximum values between **[-1,1]**. Preserves outliers

### **3. Min Max Scaling**: 
Replace values with ```(X-X_min/(X_max-X_min)```. Scale the values between 0 and 1. This transformation returns only positive numbers including 0. Mean and variance varies, min and max value range **[0,1]**

### **4. Max Absolute Scaling**: 
Replace values with ```X/(X_max)```. Scale the values between 0 and 1. This transformation returns only positive numbers including 0. Mean not centered and variance not scaled. 


### **5. Robust Scaling**: 
Replace values with ```X - X_median/(IQR)```. Centering around the median. Handle outliers as we are using IQR instead of standard deviation and mean.

```(X-X_median)/(X.quantile(0.75)-X.quantile(0.25))```

### **6. Scaling to unit norm**: 
We divide the feature vector either by Manhattan distance/l1 norm (``` |x1| +|x2|+|x3|+...+|xn|``` ) or Euclidean distance/l2 norm( ```sqrt(x1^2 + x2^2 + x3^2+...+xn^2)``` ) of the vector.

Used in clustering, text analytics when we derive features using tf-idf. 


