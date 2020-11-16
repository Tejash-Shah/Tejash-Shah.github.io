---
title: "Predict Used Car Price"
date: 2020-11-15
categories:
  - Regression Project
tags: [Machine learning, XGBoost]
excerpt: "Machine Learning, XGBoost"
---

This project contains the end-to-end implementation for predicting used car price in the USA. This project is in active mode, so I keep experimenting ideas in notebook (in notebooks folder). I got the dataset from the kaggle dataset [here](https://www.kaggle.com/austinreese/craigslist-carstrucks-data). Here are the words from the author of the data creator. Craigslist is the world's largest collection of used vehicles for sale, yet it's very difficult to collect all of them in the same place. I built a scraper for a school project and expanded upon it later to create this dataset which includes every used vehicle entry within the United States on Craigslist.

I have taken the data collected from the author and tried to implement it end-to-end including MLOps.

These are the steps I have performed:

1. Data Cleaning: First check for the plausible values in the dataset. There are couple of things which needs attention
    a) Used car price has really values in millions of dollars and if we look at the description those records/postings are from dealer saying they are willing to buy a car. So high value is not a value of a real car. 
2. Exploratory Data Analysis
3. Feature Engineering
4. Feature Selection
5. Model building
6. Model deployment using Streamlit: In progress
7. Setup CI/CD for training automation
8. Data and model versioning using DVC

Right now, this project resides in private repository. Will be open-sourcing soon.