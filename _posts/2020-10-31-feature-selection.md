---
title: "Feature Selection Notes"
date: 2020-10-31
tags: [machine learning, feature selection]
excerpt: "Machine Learning, Feature Selection"
---

# Feature-Selection

Feature Selection is a process of selecting a subset of relevant features(variable, predictors) for use in machine learning modeling.

## Why should we select features
1. Simple models are easier to interpret.
2. Short training times.
3. Enhanced generalization by reducing overfitting.
4. Reduce Variable redundancy.
5. Reduced errors of data errors during model use. 


## Filter Selection methods: 
1. **Filter methods**: Rely on characteristics of data. **Do not use machine learning model** at all (**Model agnostic**) so less computationally expensive. Very well suited for quick screen and removal of irrelevant features. Usually gives lower predictive performance than a wrapper methods. Filter methods are generally the first step in feature selection procedures.
    * **Basics**:
        - Constant 
        - Quasi Constant
        - Duplicated 
    * **Statistical measures**
        - Chi Square | Fisher score
        - Univariate methods (ANOVA)
        - Mutual Information 
    * **Correlation**

    **Two steps procedure** (Univariate):<br>
    * Rank features according to certain criteria.
      - Each feature is ranked independently of the feature space.  
    * Select the highest ranking features.

    **DRAWBACK**
    * May select redundant variables as this method doesn't consider interaction between variables.

    
         
2. **Wrapper methods**: Use machine learning models to score the feature subset. Train a new model on each feature subset that's why computationally expensive. Provide the best feature subset for a **given** machine learning model. This method is able to detect interaction between features. Subset of features work well for specific machine learning algorithm.
   * Step Forward selection
   * Step Backward selection
   * Exhaustive selection
   * Feature Shuffling (Alternative Wrapper method)
    
    **Procedure** <br>
    * Search for a subset of features.
    * Build a machine learning algorithm on subset of features. 
    * Evaluate model performance. 
    * Repeat

    **Search**
    * Forward Feature Selection <br>
    -> Add one best performing feature at a time which improves the     machine learning model until a predefined critera is met. ***Start with no feature***.
    * Backward Feature Elimination <br>
    -> ***Start with all features*** and remove the least significant feature at each iteration until criteria is reached. 

    **When to stop**<br>
    When the performance does not increase beyond a certain threshold or does not decrease or certain number of features are reached.


3. **Embedded methods**: Perform feature selection as a part of model construction process. Less computationally expensive as they fit model only once. 
    * Lasso 
    * Decision Tree derived Importance (Tree Importance)
    * Regression coefficients

    **Advantages**
    * Faster than wrapper methods
    * More accurate than filter methods
    * Detect interaction between features
    * Find the feature subset for the algorithm being trained

    **Procedure** <br>
    * Train a machine learning algorithm
    * Derive the feature importance 
    * Remove non-important features

4. **Hybrid Methods**: Hybrid methods are the combination of wrapper and embedded methods that leverages best of both worlds
    * Recursive Feature Elimination (RFE)


Feature Selection Technique should be perfomed on Training dataset to avoid overfitting.



