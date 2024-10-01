---
title: Train-test-validation split, cross-validation
description: Concept of train-test-validation split is discussed to improve model performance. In addition, a related concept of cross-validation is discussed.
author: LexXxik
date: 2024-20-14 12:00:00 +0000
categories: [fundamentals, supervised, train-test-validatation_split, cross-validation]
tags: [splits]
pin: false
math: true
mermaid: true
comments: true
pin: false
future: true
---

# Brief
We continue to explore supervised statistical learning and regression problem. In this article, I discuss different approaches to fit statistical models and why data are divided into multiple datasets: train-test split, train-test-validation split, cross-validation.

# Train-test split

We start with a regression problem and a dataset. A ``naive approach`` might be to use whole dataset for training. However, this approach runs into issue:

> **Question:** The model will perform really well on our dataset, but how do we gurantee that it generalizes to the real world?
{: .prompt-tip }

A sensible solution might be to intially split data into two groups: **training dataset**, and **testing dataset**.

### Training dataset
This will be use to train the statistical model. In the case of linear regression the datapoints are used to minimize the sums of squares. 

### Testing dataset
This is unseen data for the model and it should be never used to train a statistical model. It is kept separatelly, so the generalizability of statistical model can be tested.

At this point, we might aske what is the right split. As a rule of thumb, it is wise to retain most of the dataset for training and have a smaller portion for testing: 75% training, 25% testing.

In python, data can be split using the following code:

```python
from sklearn.model_selection import train_test_split

# Where X is a pandas datafram containing all predictors, and y is pandas series containing all dependent variables
# test_size is a float between 0 and 1 and determines the percentage of split.
# The function split data randomly into training and testing dataset
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.25)
```

# Train-test-validation split

# Cross-validation

# Conclusion
