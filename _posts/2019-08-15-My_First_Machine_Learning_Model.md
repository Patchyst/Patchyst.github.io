---
title: "Building a Neuron in Python"
date: 2019-08-15
tags: [Advanced Projects, Machine Learning, Artificial Intelligence, Python]
header:
  image: "images/machinelearningban.jpg"
excerpt: "An Introduction to Machine/deep learning and Artificial Intelligence"
---
# What is Machine Learning?
Up until this point you've probably made programs to automate tasks for you such as, do math, create encryptions, and convert complicated binary and hexadecimal into "readable" characters. Computers have given us the ability to accomplish tasks that we could have never done on our own. However, as you've noticed a computer must be explicitly told exactly what to do, but what if one could program a computer to automatically learn and improve at a task without being precisely told to do so? Well, as you've probably guessed by now I'm hinting at Machine Learning. Machine Learning uses massive data sets to allow a program to automatically enhance it's capabilities.

# Neurons and Neural Networks
## *parts of a Neuron*
![Perceptron](/images/better_image.jpg){:class="img-responsive"}
In terms of Machine Learning a neuron can be broken to a simple algebraic equation, slope-intercept form (y = mx + b). x as the input data, m as the weights, b as the bias, y as the output. **Inputs** are a set of values that represents data from a data set or another neuron, values passed in through an input serve to adjust and fine tune the weights of a neuron. **weights** control the shape of the linear regression graph, in a neural network all the "nodes" are connected via weights (e.g. output of one neuron connected to another neuron's input). When a neural network is created the weights are randomly initialized with a value that has a standard deviation of 1. As the machine learning model continues to run, loss is calculated and the weights are fine tuned and adjusted to favor certain outputs. With that in mind a weight is the strength of connection between nodes. A negative weight decreases the favorability of an output while a large weight will be a favored output. Throughout the training process these weights will be fine tuned so that the proper conclusion is reached for every output. In short you reduce the weights of the incorrect or unfavorable outputs and increase the weights of favorable or correct outputs. **bias** helps adjust the output in correspondence with the given data, but having a high bias is the result misinterpreting the underlying goal of a dataset. Unfortunately, linear regression machine learning models are examples of a parametric algorithm meaning it's pretty strict about changing it's parameters. This means that they usually have a  high bias making them bad for complex data sets. However, for simple datasets linear regression works as intended.

## Activation Functions:
An Activation or Transfer function is an essential part of every neuron, it takes the output from the previous neuron and sees if the value meets the boundaries of the preferred value. For example, if the output doesn't meet a required threshold then the neuron is not activated and the neuron becomes 0. Activation functions withhold useless outputs and assist in weight adjustment.

### *Common Activation Functions*

![Activation Function](/images/activationfunction.jpg){:class="img-responsive"}

## Forward Propagation
Forward Propagation, also known as the training step is the process of using the y=mx+b form before the activation function, then comparing the output with the desired output and getting the error.

## The Hidden layer
The Hidden Layer is the layer between the input and output nodes that takes in a set of weighted inputs and produces a weighted sum that is passed to the output nodes.

## Different Data Set types
* Training Data: The data that the model uses to learn, improve, and "train" from
* validation Data: An unbiased data set used to fine tune the model's hyperparameters
* Test Data: Used after all the training and validation data has been used. As the name suggests it is used to "test" the model's ability.

# **Building the Neuron**
Since creating a Neuron can be confusing lets it down into steps:
* 1. Take in the training data as an input
* 2. Neuron processes the data and produces a loss
* 3. Adjust the weights based off the loss
* 4. Repeat steps 1-3 until the expected output is methods

## *Modules being used in this project*
### Numpy
Numpy is a useful module to use in any Machine Learning Project because it can make massive multidimensional arrays to serve as data sets.
### Matplotlib
Matplotlib is being used because it allows us to easily graph large data sets and outputs.
