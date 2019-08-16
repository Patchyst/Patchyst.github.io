---
title: "Building Perceptron"
date: 2019-08-15
tags: [Advanced Projects, Machine Learning, Artificial Intelligence, Python]
header:
  image: "images/machinelearningban.jpg"
excerpt: "In this project I guide you through how I made my first Machine Learning Model, Perceptron. Perceptron is a fantastic introduction to the world of Machine Learning and Artificial Intelligence"
---
# What is Machine Learning?
Up until this point you've probably made programs to automate tasks for you such as, do math, create encryptions, and convert complicated binary and hexadecimal into "readable" characters. Computers have given us the ability to accomplish tasks that we could have never done on our own. However, as you've noticed a computer must be explicitly told exactly what to do, but what if one could program a computer to automatically learn and improve at a task without being precisely told to do so? Well, as you've probably guessed by now I'm hinting at Machine Learning. Machine Learning uses massive data sets to allow a program to automatically enhance it's capabilities.

# What is Perceptron?
In 1957 Frank Rosenblatt constructed what is known today as Perceptron at Cornell Aeronautical Laboratory. Perceptron is a linear classifier or more specifically a binary linear classifier that uses statistical classification. In Machine learning statistical classification is the process of using an object's features to determine which class it belongs to. A linear classifier achieves this by making a decision based on the values from a linear combination of the characteristics. As I said before Perceptron is a binary linear classifier meaning that it only classifies data into two parts; hence the bi prefix. If you're still confused lets view a Perceptron, neurons and neural networks on paper and break it down:


# Neurons and Neural Networks
## *parts of a Neuron*
![Perceptron](/images/better_image.jpg){:class="img-responsive"}
In terms of Machine Learning a neuron can be broken to a simple algebraic equation, slope-intercept form (y = mx + b). x as the input data, m as the weights, b as the bias, y as the output. **Inputs** are a set of values that represents data from a data set or another neuron, values passed in through an input serve to adjust and fine tune the weights of a neuron. **weights** control the shape of the linear regression graph, in a neural network all the "nodes" are connected via weights (e.g. output of one neuron connected to another neuron's input). When a neural network is created the weights are randomly initialized with a value between 0 and 1. As the program continues to run


## The Hidden layer
The Hidden Layer is the layer between the input and output nodes that takes in a set of weighted inputs and produces a weighted sum that is passed to the output nodes.

## Different Data Set types
* Training Data: The data that the model uses to learn, improve, and "train" from
* validation Data: An unbiased data set used to fine tune the model's hyperparameters
* Test Data: Used after all the training and validation data has been used. As the name suggests it is used to "test" the model's ability.

## Activation Functions:
Remember earlier when I mentioned earlier that a linear classifier uses linear combinations to determine which class an object belongs to? Linear activation functions use a linear combination to define the output of a node given a set of inputs.
### Sigmoid
Sigmoid is the activation function that Perceptron uses. Sigmoid equation:

![Perceptron](/images/sigmoid.jpg){:class="img-responsive"}
