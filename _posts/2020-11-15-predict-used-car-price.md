---
title: "Predict Used Car Price"
date: 2020-11-15
categories:
  - Regression Project
tags: [Machine learning, XGBoost]
excerpt: "Machine Learning, XGBoost"
---

This project contains the end-to-end implementation for predicting used car price in the USA. This project is in active mode, so I keep experimenting ideas in notebook (in notebooks folder). I got the dataset from the kaggle dataset [here](https://www.kaggle.com/austinreese/craigslist-carstrucks-data). Here are the words from the author of the data creator. Craigslist is the world's largest collection of used vehicles for sale, yet it's very difficult to collect all of them in the same place. I built a scraper for a school project and expanded upon it later to create this dataset which includes every used vehicle entry within the United States on Craigslist.

I have taken the data collected from the author and implemented it end-to-end including MLOps(In Progress).

**Columns in the dataset**: 
1. id 
2. url
3. region
4. region_url
5. price(**Target**) 
6. year
7. manufacturer
8. model
9. condition
10. cylinders
11. fuel
12. odometer
13. title_status
14. transmission
15. vin
16. drive
17. size
18. type
19. paint_color
20. image_url
21. description
22. county
23. state
24. lat
25. long

**Steps performed**:

1. **Train and Test Split**: Separate the entire data into train and test data. Our observations/findings should be based on train data and then applied on test data. 80% is saved for train and 20% is saved for test.
2. **Data Cleaning**: Check for the plausible values in the dataset. There are couple of things which needs attention
    a) Used car price has really values in millions of dollars and if we look at the description those records/postings are from dealer saying they are willing to buy a car. So high value is not a value of a real car. 
3. **Exploratory Data Analysis**
4. **Feature Engineering**: There are a lot of categorical variables for which first ```RareLabelCategoricalEncoder()``` is used to combine rare labels to a new category and following this, ```MEstimateEncoder()``` is applied to perform categorical encoding.
5. **Feature Selection**: Extensive feature selection techniques are not performed right now. Shap plots are used to see the feature importance.
6. **Model building**: Finding the best model is not the purpose right now, so ```XGBoost``` is trained without optimization.
7. **Model deployment using Streamlit**: In progress
8. **Setup CI/CD for training automation**: Working on displaying the metrics on pull request. In pull request, we specify the runner to train our machine learning model. After training, metrics are displayed in pull request so we decide if we want to push the changes in pull request to main branch or not. 
9. **Data and model versioning using DVC**: Used google drive as remote storage for data and model versioning.

Right now, this project resides in private repository. Will be open-sourcing soon. Feel free to reach out to me in case of any questions.