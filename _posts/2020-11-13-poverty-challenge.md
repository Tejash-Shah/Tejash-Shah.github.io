---
title: "Pover-T Tests: Predicting Poverty"
date: 2020-11-13
categories:
  - Binary Classification Project
tags: [machine learning, XGBoost, drivendata competition]
excerpt: "machine Learning, XGBoost, drivendata competition"
---

This repo contains the solution for the challenge hosted by drivendata for predicting poverty

---- Information from driven data ----

The data for this competition comes from The World Bank Development Data Group.

With funding from the World Bank's Knowledge for Change Program, this competition aims to engage data scientists from developing countries and apply a cost-effective solution to testing a diverse set of approaches to poverty prediction.

The surveys used to come from three developing countries. Each country offers a different demographic makeup, so successful poverty prediction across these countries will help identify a robust set of predictors that can be used in future poverty measurement efforts.

--- Data Preprocessing ---

1. Standardization
2. Encoding
3. Column Enforcement in train and test set
4. Replacing missing values

--- Sampling ---

SMOTE

---- Dimensionality Reduction ---

1. SVD
2. PCA

--- Algorithm Experimented ---

1. Random Forest
2. Logistic Regression
3. AdaBoost Classifier
4. Gradient Boosting
5. Decision Tree
6. Gaussian NB
7. Extra Tree Classifier
8. XGBoost

--- Winning Algorithm ---

XGBoost without any sampling or dimensionality reduction

Please visit this github link for notebook and related info: https://github.com/Tejash-Shah/Poverty-challenge-on-Drivendata