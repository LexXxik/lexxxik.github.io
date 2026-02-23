---
title: Feed Forward Neural Networks
description: A mathematical description of the feed forward neural network is provided in this article.
author: LexXxik
date: 2026-02-22 12:00:00 +0000
categories: [fundamentals, neural networks]
tags: [Neural Networks]
pin: false
math: true
mermaid: true
comments: true
pin: false
future: true
---

# Brief

# Architecture of Neural Network (NN)

Fundamentally, **Neural Network** is a vector function that takes input $x\in\mathbb{R}^{m}$ and produces output $o\in\mathbb{R}^{n}$ for $m,\; n \in \mathbb{N}$. Mathematicaly, we write 
$$
F_{\theta}: \mathbb{R}^{m} \to \mathbb{N}, \; x \mapsto o,
$$
where $\theta$ is a parameter space.

Let's unpack this definition. $m$ and $n$ simply describe the sizes of input and output. If the neural network is used to perdict height of participants, based on demographic data (education, income, home adress, gender) then $m=4$ and $n=1$. As we have 4 inputs and 1 output. $F_\theta$ is a grey box that takes us from the inputs to the output and $\theta$ is a collection of parameters (numbers) that produces these results.

In the following discussion we start by considering a single unit of Neural Networks called **Neuron**. These Neurons are then composed into a single layer of specified **width**, which is the number of neurones in the layer. Lastly we will consider a multi-layer neural network where the number of layers is called **depth** of neural network. 

## Single Unit (Neuron)



## Single Layer

## Multiple Layers

# What is $\sigma$?

# Evaluating performance

# Back propagation

# Conclusion
