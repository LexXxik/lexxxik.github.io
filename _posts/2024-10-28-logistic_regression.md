---
title: Logistic Regression & Classfication problem
description: This is the first article dealing with classification problem and discusses logistic regression as a tool to predict qualitative variables.
author: LexXxik
date: 2024-10-28 12:00:00 +0000
categories: [fundamentals, supervised, classification]
tags: [Classification]
pin: false
math: true
mermaid: true
comments: true
pin: false
future: true
---

# Brief
In this lesson, I cover what a **classification problem** is, and how it can be adressed using **logistic regression**. In particular, I discuss what a baye's treshold is to decide on predictions. I also discuss likelihood, loss-function, and gradient descent to estimate parameters of logisitc regression

# Classification problem
Imagine that you work at Starbucks. There is a Starbucks app that enables customer's to earn points and some customers have it while others do not. Each purchase at Starbucks is recorded and it includes the price that was paid as well as whether customer had the app, or not. Your task as a data analyst is to develop a statistical model that predicts whether the customer has an app, or not based on the money they spent. In this case:

- independent variable is continuous
- dependent variable is qualitative

This is a simple **classification problem** with two categories: has Starbucks app, does not have Starbucks app.

A good attempt to tackle the problem would be to try and predict the **probability** that customer has the app given spent money. In this case the statistical model is required to have values between 0 and 1. In addition, an arbitrry value called **bayesian treshold** must be chosen. If the probability is above the treshold, then the model predicts that the customer has an app. If the probabilty is below the treshold, then customer is predicted not to have an app.

# Logisitc regression

Logistic regression is a two-parameter model for solving classification problem. Assume the probability density function:

$$
p(x) = \frac{e^{\beta_0 + \beta_1 X}}{1+e^{\beta_0 + \beta_1 X}} = \frac{1}{1+\exp^{-(\beta_0 + \beta_1 X)}}
$$

where $X$ is dependent variable and $\beta_0,\; \beta_1$ are model parameters to be estimated. 

Note that as $X\to \infty$ the negative exponential goes to 0, so $p(X)\to 1$. However, as $X\to - \infty$ then $p(X)\to 0$. This is feature required by classification problem.

## Log-odds

A useful quantity to consider related to logistic regression is **log-odds**. 

Recall that $p(X)$ gives the probability of positive outcome. Then $1-p(X)$ gives the probability of negative outcome and so the ratio

$$
\frac{p(X)}{1-p(X)}
$$

gives **odds** of positive outcome. It is a quantity between $0$ and $\infty$. Taking a logarithm we obtain

$$
\ln\left( \frac{p(X)}{1-p(X)}\right) = \beta_0 +\beta_1 X
$$

## Likelihood 

In order to fit logistic regression to the data it is paramount to estimate parameters $\beta_0, \; \beta_1$. First assume that $Y$ is a dependent variable and $y_i$ is value of $i$ th observation, i.e. either 0, or 1. Then $X$ is the independent variable and $x_i$ is the value of $i$ th obesrvation. Then 

$$
P(Y=1 | X) = p(X) \text{ and } P(Y=0 | X) = 1-p(X)
$$

are probabilities of positive, and negative outcome respectively. Then define a **likelihood** function

$$
L(p_i | Y) = P(Y = y_i) = p_i^{y_i} (1-p_i)^{1-y_i},
$$

where $p_i = p(X=x_i)$. The likelihood function outputs probability that logistic regression predicts associated with data point $(x_i,y_i)$. If the logistic regression makes a perfect prediction at data point $(x_i,y_i)$, then the likelihood function is 1. It is $0$ if model misscategorizes observation.

### Maximum Likelihood estimation

A reasonable requirement for the best possible model would be to maximize likelihood across all data points, i.e. to find maximum of the quantity:

$$
L(p | Y) = \prod_{i} L(p_i | Y) = \prod_{i} p_i^{y_i} (1-p_i)^{1-y_i}.
$$

To this end we would have to calculate derivative of $L(p | Y)$ which would require to apply product rule repeatedly. Hence, it is beneficial to introduce a **log-likelihood** 

$$
l(p | Y) = - \ln (L(p | Y)) = - \sum_{i} \ln(p_i^{y_i} (1-p_i)^{1-y_i}) = - \sum_{i} y_i\ln(p_i) +  (1-y_i)\ln(1-p_i) 
$$

and minimize it instead. Note that the derivative of a sum is a lot easier to calculate. 

However, it is advised to average the log-likelihood by the number of data points $N$, so that log likelihoods can be compared as the number of datapoints increases: 

$$
Loss(p | Y) = \frac{1}{N}l(p | Y)
$$

We proceed by finding the minimum let $m\in\{ 0, 1\}$, then we attempt to calculate

$$
\frac{d \;l(p | Y)}{d\; \beta_m} = 0.
$$

We have 

$$
\frac{d \;l(p | Y)}{d\; \beta_m} = - \sum_{i} \left( y_i\frac{1}{p_i} +  (1-y_i)\frac{1}{1-p_i}\right)\frac{d \;p_i}{d\; \beta_m}
$$

and

$$
\frac{d \;p_i}{d\; \beta_m} = \frac{1}{(1+e^{-(\beta_0+\beta_1 x_i)})^2}e^{-(\beta_0 + \beta_1 x_i)}x_{i,m} = p_i(1-p_i)x_{i,m},
$$
where $x_{i,m} = 1$ if $m=0$ and $x_{i,m} = x_i$ otherwise. Hence, 

$$
\frac{d \;l(p | Y)}{d\; \beta_m} = - \sum_{i} \left( y_i(1-p_i) +  (1-y_i)p_i\right) x_{i,m} = 0
$$

However, this cannot be rearranged to obtain analytical expression for $\beta_0, \; \beta_1$. Therefore. a numerical algorithm such as gradient descent must be used to find approximate minimum and find estimates for $\beta_0, \; \beta_1$

## Gradient Descent

To find approximation of $\beta_0, \beta_1$ we resort to a technique called gradient descent. Assume a function $F(\bm x)$ that describes a hyper-surface where $\bm x$ is a point of vector space. Now, consider $\nabla F(\bm x)$, a gradient of $F(\bm x)$, it gives the direction of fastest growth of $F(\bm x)$. Hence, $-\nabla F(x)$ gives a direction of **fastest descent**.

Therefore, we can define a sequence $\{ \bm x_n \}_{n=0}^N$ such that

$$
\bm x_{n+1} = \bm x_n - \gamma \nabla F(\bm x_n),
$$

where $\gamma$ is the step size and $N$ is the maximum number of steps. 

## Estimating parameters of Logistic regression

Ofcouse, for our purposes we consider $\bm \beta = (\beta_0, \beta_1)$ with $Loss (p | Y)$. Then consider a sequence of vectors $\{ \bm \beta_n \}_{n=0}^N$ where $N$ is a maximum number of steps and with an intial guess $\bm \beta_0$ such that

$$
\bm \beta_{n+1} = \bm \beta_n - \gamma \nabla Loss(p | Y),
$$
where $\gamma$ is a step size. In particular, note that

$$
\nabla Loss(p | Y) = \frac{1}{N_{\text{data}}}\left( \frac{d \;l(p | Y)}{d\; \beta_0}, \frac{d \;l(p | Y)}{d\; \beta_1} \right).
$$

Hence, we approximate a location of minimum of the loss function in the vector space of parameters $(\beta_0, \beta_1)$.

# Conclusion
In this section, I introduced simple classification problem where we predict qualitative variable. I also discussed baye's treshold for making the classification. Then I introduced probability density function of logistic regression with two parameters $\beta_0, \beta_1$. Then I discussed how likelihood function and log-likelihood are linked and their relation to estimating parameters. Finally, I introduced gradient descent as a means to approximate location of the minimum of loss function.