---
date: 2019-06-29 12:20:00
title: Random Forest Classification
subtitle: Along with its implementation in Python
description: Random Forest Classification
image: https://cdn-images-1.medium.com/max/716/0*XaGgN0G--22Lk26h.png
optimized_image: https://cdn-images-1.medium.com/max/716/0*XaGgN0G--22Lk26h.png
category: machine-learning
tags:
  - technology
  - machinelearning
  - datascience 
  - deeplearning 
  - algorithms
layout: single
comments: true
author_profile: true
toc: true
---

In this blog we’ll try to dig deeper into Random Forest Classification. Here we will learn about ensemble learning and will try to implement it using Python.

You can find the code over [here](https://github.com/afrozchakure/Internity-Summer-Internship-Work/tree/master/Blogs/Random_Forest_Classification).

## Random Forest Classifier :
It is an ensemble tree-based learning algorithm. The Random Forest Classifier is a set of decision trees from randomly selected subset of training set. It **aggregates the votes from different decision trees** to decide the final class of the test object.

## Ensemble Algorithm :
Ensemble algorithms are those which **combines more than one algorithms of same or different kind for classifying objects.** For example, running prediction over Naive Bayes, SVM and Decision Tree and then taking vote for final consideration of class for test object.

<figure>
<center><img src="https://miro.medium.com/max/574/0*a8KgF1IINziv7KIQ.png" alt = "Structure of Random Forest Classification">
<figcaption>Structure of Random Forest Classification</figcaption>
</center>
</figure>

## Types of Random Forest models:
1. Random Forest Prediction for a **classification problem:**
f(x) = majority vote of all predicted classes over B trees
2. Random Forest Prediction for a **regression problem:**
f(x) = sum of all sub-tree predictions divided over B trees

### An Example of Random Forest Classification :

<figure>
<center><img src="https://miro.medium.com/max/647/0*edh34CKyDT7sDHgL.png" alt = "An Example of Random Forest Classification :">
<figcaption>An Example of Random Forest Classification</figcaption>
</center>
</figure>

### Nine Different Decision Tree Classifiers

<figure>
<center><img src="https://miro.medium.com/max/594/0*pCV1ZFzLBTJN5NhE.png" alt = "Aggregated result for the 9 Decision Tree Classifiers">
<figcaption>Aggregated result for the 9 Decision Tree Classifiers</figcaption>
</center>
</figure>

The 9 decision tree classifiers shown above can be aggregated into a random forest ensemble which **combines their input** (on the right). The horizontal and vertical axes of the above decision tree outputs can be thought of as features x1 and x2. At certain values of each feature, the decision tree outputs a classification of “blue”, “green”, “red”, etc.

These above **results are aggregated**, through **model votes or averaging**, into a single ensemble model that ends up outperforming any individual decision tree’s output.

## Features and Advantages of Random Forest :
1. It is one of the most accurate learning algorithms available. For many data sets, it produces a highly accurate classifier.
2. It runs efficiently on large databases.
3. It can handle thousands of input variables without variable deletion.
4. It gives estimates of what variables that are important in the classification.
5. It generates an internal unbiased estimate of the generalization error as the forest building progresses.
6. It has an effective method for estimating missing data and maintains accuracy when a large proportion of the data are missing.

## Disadvantages of Random Forest :
1. Random forests have been observed to overfit for some datasets with noisy classification/regression tasks.
2. For data including categorical variables with different number of levels, random forests are biased in favor of those attributes with more levels. Therefore, the variable importance scores from random forest are not reliable for this type of data.

### Implementation of Random Forest Classification on real life dataset:
### 1. Importing Python Libraries and Loading our Dataset into a Data Frame

<figure>
<center><img src="https://miro.medium.com/max/329/0*2_R6v-mCUONNtnOU.png" alt = "Importing Python libraries">
</center>
</figure>

### 2. Splitting our dataset into training set and test set
<figure>
<center><img src="https://miro.medium.com/max/700/0*HkNHZX-UXOlCQLhk.png" alt = "Importing Python libraries">
</center>
</figure>

### 3. Creating a Random Forest Classification model and fitting it to the training data
<figure>
<center><img src="https://miro.medium.com/max/700/0*HkNHZX-UXOlCQLhk.png" alt = "Importing Python libraries">
</center>
</figure>


### 4. Predicting the test set results and making the Confusion matrix
<figure>
<center><img src="https://miro.medium.com/max/442/0*eG-NEvR0Qif2WRw1.png" alt = "Importing Python libraries">
</center>
</figure>

## Conclusion :
In this blog we have learned about the Random forest classifier and its implementation. We looked at the ensembled learning algorithm in action and tried to understand what makes Random Forest different from other machine learning algorithms.


