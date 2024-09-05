---
title: Statistical learning
description: How are techniques in data science divided?
author: LexXxik
date: 2024-09-05 12:00:00 +0000
categories: [fundamentals, statistical_learning, supervised, unsupervised]
tags: [Foundational]
pin: true
math: true
mermaid: true
comments: true
pin: false
future: true
---

# Brief
In this article, we look at the main distinction between statistical techniques in data science, namely, supervised and unsupervised learning.

# Statistical Learning

Given a data set, we can perform two kinds of analysis: **predictions** and **pattern identification**. Statistical learning is an umbrella term that encompasses both of these actions.

When looking at predictions, we make a choice of **independent** and **dependent** variables. The aim is to use independent variables to predict dependent variables using a **statistical model**.

### Example: predicting sales (prediction)

Imagine that we are running an online store. We can measure two variables: advertisement budget and sales. Visualizing the data on a graph, we might notice a pattern that suggests a linear relationship between these variables. Assuming that our goal is to predict future sales based on the advertisement budget, we can use the pattern we spotted to make a prediction.

In this example, the advertisement budget is the independent variable used to predict sales, the dependent variable. The prediction is possible by using the pattern in the data that was spotted. An assumption was made about how the advertisement budget relates to sales. This is a statistical model. Since we assumed the model based on the graph, we are using **supervised learning**.

### Example: Instagram users (pattern recognition)

Imagine that you are an influencer running an Instagram account, and you are about to launch new merch. However, you have never sold anything to your followers, so there is no way to predict sales.

However, you can try to identify what kinds of followers you have and group them by post engagement, number of comments, number of likes, age, gender, etc. A reasonable question is, how many distinct groups of followers are there? What are the clustering properties of these groups?

Instead of visualizing the data and choosing independent and dependent variables, you approach the problem differently: you let the computer find the patterns. You give it a simple instruction to group users based on their similarity. This is an example of **unsupervised learning**.

## Supervised Learning

Supervised learning is a set of statistical techniques that separate variables into dependent and independent variables and choose a statistical model to make predictions. The essential point is that there is a variable that is being predicted and a model of the relationship that is being assumed.

Examples of these statistical techniques include **regression** and **classification problems**. In a regression problem, the dependent (predicted) variable is quantitative, such as temperature. In classification problems, it is qualitative, such as categorizing images into cats and dogs.  

## Unsupervised Learning

Unsupervised learning is also a set of statistical techniques, but there is no separation between dependent and independent variables. Instead, the statistical techniques attempt to uncover patterns in the data.

An example is a **clustering technique**, such as grouping accounts on social media by the tags used in their posts. The key is that no statistical model is assumed, and the ``learning`` is left to the algorithm.

## Conclusion

Statistical learning is a set of statistical techniques applied to data. There is a further division into supervised and unsupervised learning. In supervised learning, there is a clear separation between variables we try to predict and variables used for the prediction. On the other hand, unsupervised learning uncovers the relationships in the data.
