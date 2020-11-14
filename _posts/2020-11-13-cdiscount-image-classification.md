---
title: "CDiscount Image Classification Challenge"
date: 2020-11-13
categories:
  - Image Classification Project
tags: [deep learning, CNN, kaggle competition]
excerpt: "deep Learning, CNN, kaggle competition"
---

In this challenge, a model has been developed that will classify the products based on their images. The dataset which is provided has following characteristics:
1. 9 million products
2. More than 15 million images having 180x180 resolution
3. More than 5000 categories

**Dataset Description**

1. train.bson (Size: 58.2 GB) - This is the main dataset which is provided to work on. It contains a list of 7,069,896 dictionaries, one per product. Each dictionary contains a product id, the category id of the product. Images are presented in the form of binary
string which corresponds to binary representation of the image in JPEG format.

2. train_example.bson (616KB) – This is the dataset we are supposed to work on, initially. It contains the first 100 records of train.bson so that we can start exploring the data before moving on to train.bson

3. test.bson (Size: 14.53 GB) – This is the dataset on which prediction has to be made. It contains a list of 1,768,182 products in the same format as train.bson except there is not category id

**Algorithms Implemented**

1. Baseline model having 3 Convolution layer Deep learning model
2. VGG 16 
3. VGG 19
4. ResNet50
5. Inception
6. Keras CNN model
7. VGG19 with real time data augmentation and convolution layer tuning

**Dependencies**

1. Pandas
2. Numpy
3. TensorFlow
4. Matplotlib
5. Pymongo
6. Keras
7. os
8. io
9. PIL


Please visit this github link for notebook and related info: https://github.com/Tejash-Shah/CDiscount-Image-Classification-Challenge 

