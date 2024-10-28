---
title: Ridge & Lasso regularization
description: How to discourage large coefficents in linear regression? How to perform variable selection? These questions are answered in this article.
author: LexXxik
date: 2024-10-7 12:00:00 +0000
categories: [fundamentals, supervised, linear_regression , regularization, cross-validation]
tags: [Regression]
pin: false
math: true
mermaid: true
comments: true
pin: false
future: true
---

# Brief
We continue to explore supervised statistical learning and regression problem. In particular, if there are multiple predictors in the linear regression model, we might want to limit their magnitude, i.e. regularize them. Furthermore, it is useful to slect only those predictors that significantly contribute to dependent variable.

# Regularization
Recall that for linear regression we minimized Residual Sums of Squares (RSS):

$$
\text{RSS} = \sum_{i=1}^n (y_i - \beta_0 - \sum_{j=1}^J \beta_j x_{ij})^2,
$$

assuming $J$ predictors and coefficents $\beta_0, \beta_1, \ldots , \beta_J$. To perform regularization the following **loss function** is minimized (in the same way as RSS was minimized):

$$
L(\beta) = \text{RSS} + \lambda \text{L}_{reg}
$$

where $\lambda$ is a hyperparameter to be chosen and $\text{L}_{reg}$ is the term that depends on specific regularization.

## Ridge regularization
In the case of ridge regularization the last term is given as follows:

$$
\text{L}_{reg} = \sum_{j=1}^J \beta_j^2 .
$$

It is straight forward to minimize resulting function by equaling the derivative to 0 and rearrangin for $\beta $s. Because analytic solution is available, ridge regularization is fast to compute relative to Lasso. However, ridge regularization does not preform selection of predictors.

In python the following function can be used to perform ridge regulariuzation: 
```python
from sklearn.linear_model import Ridge
import numpy as np

# alpha is equivalent our parameter lambda
clf = Ridge(alpha=1.0)
# Fit ridge regression predictors X and dependent variables y
clf.fit(X, y)
```
## Lasso Regularization
This regularization has

$$
\text{L}_{reg} = \sum_{j=1}^J | \beta_j | .
$$

Because of appearence of absolute value, there is no derivative at $\beta_j$ at 0 and so no analytical expression. Instead the parameters $\beta_j$ have to be estimated with iterative numerical methods. This makes Lasso regularization slower to compute, but it performs variable selection in contrast to Ridge regression. Hence, it is a regulazation of choice to many data scientists. 

In Pyhton thi is implemented as
```python
from sklearn.linear_model import Lasso
import numpy as np

# alpha is equivalent our parameter lambda
clf = Lasso(alpha=0.01)
# Fit Lasso regression predictors X and dependent variables y
clf.fit(X, y)
```
## Selecting $\lambda$
In both Ridge and Lasso regression a hyperparameter $\lambda$ must be chosen. To that end we can use test-train-validation split. Mutliple models with varying $\lambda$ s are trained on the taining set and then MSE is calculated on the validation set. Then we pick $\lambda$ corresponding to the lowest MSE.

In order to prevent overfitting to validation set, cross-validation can be used instead. In that case we pick lambda that has lowest average MSE across multiple folds.
# Conclusion
Regularization is introduced to discourage overly large values of coefficients in our model and to perform variables selection. In this article we discussed loss function related to regularization and two regularizations: ridge, and lasso. Lasso performs variable selection, but is more expensive to compute than Ridge regression. 