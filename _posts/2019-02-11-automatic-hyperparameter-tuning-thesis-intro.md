---
title: "Automatic Hyperparameter Tuning for Distributed Machine Learning"
layout: post
date: 2019-02-11 18:15
tag:
- machine learning
- hyperparameter optimization
- deep learning
- distributed systems
- AutoML
projects: true
description: "A brief introduction to my Master Thesis project."
category: project
author: sinash
externalLink: false
---

**TL;DR:** This post is a brief introduction to the topic of my Master Thesis project for which I'm working at the Computer Systems Laboratory (CSL) of [RISE SICS](https://sics.se) and [Logical Clocks AB](https://www.logicalclocks.com) under the supervision of [Jim Dowling](https://www.kth.se/profile/jdowling?l=en). In short, we want to design and develop a framework - and possibly a set of algorithms - for **automatic hyperparameter tuning** of machine learning and deep learning models **in a distributed manner**, while **maximizing the resource utilization** of our clusters.

*Last Update: February 11, 2019*

---

The *classic* definition of a *hyperparameter* of a machine learning model is a parameter of the model which we do not learn during the training process - we have to set its value before the training begins. Examples of familiar hyperparameters include learning rate, dropout, number of layers of the neural network, number of neurons in each layer, convolution filter width, or even the learning algorithm itself.

The problem - well, the challenge -  with having model hyperparameters is that each hyperparameter introduces a design decision, and making these decisions usually requires domain knowledge, theoretical expertise, and a lot of expensive trials and errors (among other things). That's why e.g. some of the state-of-the-art deep learning models are the results of several months of hand-tuning and experiments. Let's not forget that usually training a decent deep learning model might take several hours, days, or weeks, so you really want to have good faith in your chosen hyperparameters. 

Current state-of-the-art machine learning and deep learning models may consist of several hyperparameters, each having a significant influence on the performance of the model, training speed, and things like that. Even basic machine learning models, such as linear regression, are very sensitive to their hyperparameters - we've all heard the story about how setting the wrong value for the learning rate might leave us [wandering in the valley](https://thelaziestprogrammer.com/sharrington/math-of-machine-learning/gradient-descent-learning-rate-too-high).

Given well-prepared and suitable training and test datasets, the typical machine learning process consists of the following steps:
1. Choose a set of hyperparameter values.
2. Initiate the training process, and go over the training data to optimize the model parameters (e.g. the weights of neurons).
3. Evaluate the model.
4. If things don't look good enough (which is often the case), we change the values of our hyperparameters and do it all over again.

We repeat this process until we achieve a desirable performance, which usually translates to a very low test error. In contrast to model parameters that we try to **learn** in step 2 (a process which usually involves computing derivatives or *gradients*), we usually do not know how a particular choice of a hyperparameter might affect our model performance. Thus, we can think of our machine learning (or deep learning, if you prefer) model as a black-box in relation to its hyperparameters. We don't even have a closed-form function of the hyperparameters to be able to compute its derivatives (and optimize on them), so, as you might have already guessed, a general practice for automatic hyperparameter tuning is using black-box optimization, by which we most often mean [derivative-free optimization](https://en.wikipedia.org/wiki/Derivative-free_optimization). The celebrities here are random search (naive!), grid search, evolutionary methods, and Bayesian optimization.

If we can somehow eliminate the need for hand-picking the hyperparameter values (aka "design decisions"), we will get one step closer to having truly **automated** machine learning systems and pipelines, which is the main focus of a trending field known as AutoML. The immediate consequence of automating the machine learning pipelines is that more and more people can leverage the benefits that machine learning and deep learning provide, while avoiding all the hassle and specific technicalities of training and optimizing models - our machines will be capable of [learning how to learn](https://bair.berkeley.edu/blog/2017/07/18/learning-to-learn/), and the *classic* definition of hyperparameters would be obsolete.

Black-box optimization has been studied for years by statisticians and machine learning scientists. However, (here it comes!) the recent advances in deep learning, realized mainly thanks to the emergence of giant data sets and the wealth of computation resources and data-intensive computing techniques, has led to the need for faster, more efficient machine learning pipelines, and this requires blending ideas from the fields of distributed systems and machine learning. We want to be able to harness the full power of our clusters (GPUs are expensive!) to find the optimal (or sufficiently close to optimal) values for our hyperparameters, as fast as possible. 

To this end, we aim to develop a framework and possibly a suite of algorithms specifically designed for automatic, distributed tuning of hyperparameters for machine learning and deep learning. The results of this project will be available open-source and added to the [Hops Big Data & AI platform](hops.io).

In the meantime, make sure you check out [this curated list of good resources on AutoML](https://github.com/ssheikholeslami/automl-resources) on GitHub!