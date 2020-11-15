---
title: "Variable Transformation"
date: 2020-11-14
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
---

Linear models assume variables are normally distributed

Normality can be checked using Histogram and Q-Q plots.

We try multiple transformations and see which one performs the best


1. Logarithmic ([np.log(X)](https://numpy.org/doc/stable/reference/generated/numpy.log.html)/[np.log1p(X)](https://numpy.org/doc/stable/reference/generated/numpy.log1p.html))
2. Exponential or Power Transformation ([np.sqrt](https://numpy.org/doc/stable/reference/generated/numpy.sqrt.html)/[np.power(X,1/2)](https://numpy.org/doc/stable/reference/generated/numpy.power.html), np.power(X,1/3) or any exponent) 
3. Reciprocal
4. Box-Cox(Exponential transformation, defined for X>0, [stats.boxcox(X)](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.boxcox.html))
5. Yeo-Johnson(Exponential Transformation, [stats.yeojohnson(X)](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.yeojohnson.html)) 
