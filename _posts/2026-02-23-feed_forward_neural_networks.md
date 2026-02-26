---
title: Feed Forward Neural Networks
description: A mathematical description of the feed forward neural network is provided in this article.
author: LexXxik
date: 2026-02-23 12:00:00 +0000
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
F_{\theta}: \mathbb{R}^{m} \to \mathbb{R}^n, \; x \mapsto o,
$$

where $\theta$ is a vector of parameters facilitating the transition.

The two numbers $m$ and $n$ describe the sizes of input and output. If the neural network is used to perdict height of participants, based on demographic data (education, income, home adress, sex) then $m=4$ and $n=1$. As we have 4 inputs and 1 output. $F_\theta$ is a grey box that transforms the inputs to the output.

In the following discussion we start by considering a single unit of Neural Networks called **Neuron**. These Neurons are then composed into a single layer of specified **width**, which is the number of neurones in the layer. Lastly we will consider a multi-layer neural network. The number of layers is called **depth** of neural network. 

## Single Unit (Neuron)

**Neuron** is the simplest unit of a neural network (Figure 1). It takes inputs $x_1, \dots, x_m$, transforms the inputs via weights $w_1, \dots, w_m$ and a bias $b$ to produce an output $o$. The final output $o$ is produced by activation function $f$. Mathematically, this can be written as

$$
o = f (w_i x_i + b),
$$

where Einstein's summation convention was employed. Here, $f: \mathbb{R} \to \mathbb{R}$ 

![Figure 1](../blog_images/2026-02-22/neurone.png)
_Figure 1: Neuron with multiple inputs $x$, output $o$, bias $b$ and activation function $f$._

## Single Layer

In order to produce multiple outputs, we must add multiple neurones into series (Figure 2).

![Figure 2](../blog_images/2026-02-22/single_layer.png)
_Figure 2: Single layer of neurones with inputs $x$, multiple outputs $o$, bias $b$ and activation function $f$._

The only difference in mathematical formulation from the single neuron case the the addion of the extra index accounting for each of the nuerones. Hence, the set of weights can be organize into matrix $w_{\alpha i}$ for $i \in \{ 1, \dots, m \}$ and $\alpha \in \{ 1, \dots, n\}$. The mathematical formulation becomes: 

$$
o_\alpha = f (w_{\alpha i} x_i + b_\alpha),
$$
where $f$ is applied element-wise for each index $\alpha$. 

## Multiple Layers

# What is an activation function $f$?

# Evaluating performance

# Back propagation

# Conclusion
