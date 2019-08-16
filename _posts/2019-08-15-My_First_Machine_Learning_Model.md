---
title: "Building Perceptron"
date: 2019-08-15
tags: [Advanced Projects, Machine Learning, Artificial Intelligence, Python]
header:
  image: "images/machinelearningban.jpg"
excerpt: "In this project I guide you through how I made my first Machine Learning Model, Perceptron. Perceptron is a fantastic introduction to the world of Machine Learning and Artificial Intelligence"
---
# What is Machine Learning?
Up until this point you've probably made programs to automate tasks for you such as, do math, create encryptions, and convert complicated binary and hexadecimal into "readable" characters. Computers have given us the ability to accomplish tasks that we could have never done on our own. However, as you've noticed a computer must be explicitly told exactly what to do, but what if one could program a computer to automatically learn and improve at a task without being precisely told to do so? Well, as you've probably guessed by now I'm hinting at Machine Learning. Machine Learning usually uses massive data sets to allow a program to automatically enhance it's capabilities.

# What is Perceptron?
In 1957 Frank Rosenblatt constructed what is known today as Perceptron at Cornell Aeronautical Laboratory. Perceptron is a linear classifier or more specifically a binary linear classifier that uses statistical classification. In Machine learning statistical classification is the process of using an objects features to determine which class it belongs to. A linear classifier achieves this by making a decision based on the values from a linear combination of the characteristics. As I said before Perceptron is a binary linear classifier meaning that it only classifies data into two parts; hence the bi prefix. If you're still confused lets view a Perceptron Neuron on paper and break it down:

![Perceptron](/images/nuer.jpg){:class="img-responsive"}

The first thing you probably recognized were the inputs, just like any other input this is where the data is passed into the neuron, whether that data be from a training, validation, or test data set (I'll provide a brief explanation of the different data set types soon). Next we have the weights which are the lines that connect the nodes between layers. To begin, weights are randomly initialized or gauged and through the process of backpropagation, the weights are usually random numbers that have a mean of 0 and a standard deviation of 1. Weights are usually the strength of connection between the two nodes.

## The Hidden layer
The Hidden Layer is the layer between the input and output nodes that takes in a set of weighted inputs and produces a weighted sum that is passed to the output nodes.

## Different Data Set types
* Training Data: The data that the model uses to learn, improve, and "train" from
* validation Data: An unbiased data set used to fine tune the models hyperparameters
* Test Data: Used after all the training and validation data has been used. As the name suggests it is used to "test" the model's ability.
