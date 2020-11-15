---
title: "Mixed Variables"
date: 2020-11-15
categories:
  - Feature Engineering
tags: [machine learning, feature engineering]
excerpt: "Machine Learning, Feature Engineering"
--- 

Variables that contain numbers and categories in values


4.1. Number or labels in different observation <br>
a) Number of Credit Account => [1-100, U, T, M] where U=Unknown, T=Unverified, M=Unmatched <br>
b) Number of missed payments => [1-3, D, A] where D=Defaulted, A=Arrangements <br>

4.2. Number and labels in same observation. For example, Cabin(Ticket), ticket number(TItanic), Vehicle Registration, etc...


To engineer mixed variables, separate out numerical and categorical into different column.