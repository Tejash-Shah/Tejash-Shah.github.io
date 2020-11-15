---
title: "Missing Data Imputation"
date: 2020-11-14
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
---


 Imputation is the act of replacing missing data with statistical estimates of the missing values. The goal of any imputation technique is to produce a complete data-set that can be used to train machine learning models.

 | Numerical Variable | Categorical Variables | Both |
| :---:         |     :---:      |         :---: |
| Mean / Median Imputation  | Frequent category imputation (Mode imputation)     | Complete Case Analysis   |
| Arbitrary value imputation      | Adding a “missing” category       | Adding a “Missing” indicator       |
| End of tail imputation          |                                   | Random sample imputation     |

 # Complete Case Analysis

 Complete-case analysis (CCA), also called **"list-wise deletion"** of cases,is dropping observations where values in any of the features are missing. In Complete Case Analysis, we analyse only those observations for which there is information in all of the variables in the data-set. **Suitable for categorical and numerical variables**

 ## Assumption
 1. Data is missing completely at random (MCAR). When data is MCAR, excluding observations with missing information is in essence the same as randomly excluding some observations from the dataset. Therefore the dataset after CCA is a fair representation of the original dataset.

## Advantages
1. Simple<br>
2. No data manipulation required<br>
3. **Preserves the distribution of the variables since removing null data is like removing random observations**

## Limitations
1. In production model will not know how to perform when faced with missing value
2. Could exclude a large fraction of dataset
3. Could create a biased dataset if complete cases differ from missing data
4. Dropped information could be informative

## When to use CCA
1. Data is missing at random
2. No more than 5% of the dataset contains missing data

# Mean / Median Imputation

Mean / median imputation consists of replacing all missing values with mean or median. **Suitable for numerical variables**

If the variable is normally distributed the mean and median are approximately the same.
***If the variable is skewed, median is a better representation***

## Assumptions
Data is missing completely at random

## Limitations
1. Distorts the original variable distribution
2. Distorts the original variance
3. Distorts the covariance with the remaining variables of the dataset
4. The higher the percentage of NA, the higher the distortion

## When to use Mean / Median Imputation

1. Data is missing completely at random (MCAR)
2. No more than 5% of the dataset contains missing data
3. ***Typically, mean / median imputation is done together with adding a binary "missing indicator" variable to capture those observations where the data was missing, thus covering 2 angles: if the data was missing completely at random, this would be captured by the mean /median imputation, and if it wasn't this would be captured by the additional "missing indicator" variable. Both methods are extremely straight forward to implement, and therefore are a top choice in data science competitions.***

The mean or median value should be calculated only from the train set and used to replace NA in both train and test sets to avoid over-fitting


## **NOTE: PLEASE READ**
Higher the percentage of missing values in a feature, higher is the distortion of the distribution. Replacing high number of missing values will give a peak at mean/median value and thus decreasing variance of the data. If the variance decreases, inter-quartile range will decrease and thus  look like more number of outliers. It will create artificial outliers. It also affects the covariance and correlation with other variables. **Although in theory, the assumptions should be met to minimize the impact of this imputation technique, in practice, mean / median imputation is very commonly used, even in those cases when data is not MCAR and there are a lot of missing values. The reason behind this is the simplicity of the technique**

# Arbitrary Value Imputation
 Arbitrary value imputation consists of replacing all missing values with arbitrary values.Arbitrary values could be like 0, 999, -999 (or other combinations of 9s) or -1 (if the distribution is positive).
**Suitable for numerical and categorical variables.** In Categorical variable we add new category->“Missing”

## Assumptions
1. Data is **not missing** at random (NMAR).
2. If this is the case, we want to flag the missing values with a different (arbitrary) value, instead of replacing those occurrences with the mean or the median, which represent the most common value

## Limitations
1. Distorts the original variable distribution
2. Distorts the original variance
3. Distorts the covariance with the remaining features
4. If the arbitrary value is at the end of the distribution it may mask or create outliers
5. Need to be careful not to chose an arbitrary value too similar to the mean or median (or any other common value of the variable distribution)
6. **The higher the percentage of NA, the higher the distortion**

Linear models assume that the variables are normally distributed. Arbitrary value imputation may distort the original normal distribution if the % of missing data is high. Therefore the final imputed variable will no longer be normally distributed, which in turn may affect the linear model performance. On the other hand, this technique works quite well with tree based algorithms.

The process of selecting the arbitrary value is quite manual. We need to go variable per variable,observe the distribution and min / max values, to then select the arbitrary value. It works well for a few variables, but if our datasets contain hundreds or thousands, it becomes a bit inconvenient. An alternative for automation, is to place the values at the end of the distribution.

## **NOTE: PLEASE READ**

Could mask/affect the outliers and possibly create another peak of values if number of missing values is high. Increase the variance as well.


# End of Tail Imputation
End of tail imputation is equivalent to arbitrary value imputation, but  selecting arbitrary values at the end of the variable distributions. **Suitable numerical variables** <br>
Two ways to select arbitrary values:
1. If the variable is normally distributed, we can use the mean plus or minus 3 times the standard deviation. 
2. If the variable is skewed, we can use the IQR proximity rule. 

This method is used in finance companies. When capturing the financial history of customers, in order not to assume that missing is at random, the missing data are replaced by a value at the end of the distribution.


For skewed distribution <br>
The general approach is to calculate the quantiles, and then the inter-quantile range (IQR), as follows: <br>
● IQR => 75th Quantile – 25th Quantile => Q<sub>3</sub> - Q<sub>1</sub>  <br>
● Upper limit => 75th Quantile + IQR × 1.5 => Q<sub>3</sub>  + 1.5 x IQR <br>
● Lower limit => 25th Quantile - IQR × 1.5 => Q<sub>1</sub>  + 1.5 x IQR<br>
Note, for extreme outliers, multiply the IQR by 3 instead of 1.5

Assumptions, Advantages and Limitations are same as of Arbitrary Value Imputation.

## **NOTE, PLEASE READ**
By replacing missing values with End-of-tail value, outlier are masked with high number of missing values. Distorts distribution and covariance.

# Frequent Category Imputation

Frequent Category imputation consists of replacing all missing values with the mode. **Suitable numerical and categorical variables. In practice, we use this technique with categorical variables.**

## Assumptions
1. Data is missing completely at random (MCAR)

## Limitations
1. Distortion the relation of the most frequent label with other features
2. May lead to an over-representation of the most frequent label if there is a big number of missing values
3. The higher the percentage of NA, the higher the distortions

# Missing Category Imputation
This method consists in treating missing data as an additional label or category of the variable. Replace missing value with new label/string "missing". **Most widely used and suitable method of missing data imputation for categorical variables.**

## Assumptions
1. No Assumptions

## Limitations
1. Distorts the distribution of the original feature or creates an unnecessary label category

# Random Value/Sample Imputation
Random sampling consist in taking a random observation from the pool of available observations of the variable, and using that randomly extracted value to fill the NA. **Suitable for both numerical and categorical variables.** We extract random values as many times the number of missing values

***Set seed while imputing with random values otherwise for every run, there will be different value generated***

## Advantages
1. Preserves variance of the feature
2. Does not distorts the distribution of the original feature
3. Minimal effect on outliers


## Limitations
Covariance/ Interaction between the features may or may not be preserved.
Minimal effect on outliers

# Missing Indicator
 A Missing Indicator is an additional binary feature, which indicates whether the data was missing for an observation (1) or not (0). **Suitable for numerical and categorical variables**. 

 Numerical data=> Missing value  indicator + Mean/Median Imputation <br>
 Categorical data=> Missing value indicator + Frequent Category 

## Application
sed together with methods that assume data is missing at random:
1. Mean, median, mode imputation
2. Random sample imputation

## Assumptions
Data is NOT missing at random

## Limitations
1. Increase the total number of features
2. Original feature still needs to be imputed
2. Presence of many missing indicators may end up being identical or very highly correlated

## When to use a missing indicator
Mean/ Median and mode imputation are done together with adding "missing indicator" feature thus covering 2 angles:
If the data was missing completely at random, this would be captured by the mean, median or mode imputation, and if it wasn't this would be captured by the additional "missing indicator" variable.
**Both methods are extremely straight forward to implement, and therefore are a top choice in data science competitions.**


Learn more about 
1. Iterative Imputer
2. MICE
3. KNN
4. Miss Forest
5. Fuzzy K Means clustering
[link1](https://towardsdatascience.com/why-using-a-mean-for-missing-data-is-a-bad-idea-alternative-imputation-algorithms-837c731c1008)
 <br>


