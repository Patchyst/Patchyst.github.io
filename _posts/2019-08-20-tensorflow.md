---
title: "Build a Neural Network with TensorFlow (unfinished)"
date: 2019-08-20
tags: [Advanced Projects, Machine Learning, Artificial Intelligence, Python]
header:
  image: "images/tensor.jpg"
excerpt: "Use a module developed by Google to program a neural network"
---
## TensorFlow
In this Project well be using TensorFlow to program and train our own accurately built neural network. TensorFlow is a library developed by Google with the soul purpose of accelerating and simplifying the process of building and training machine learning models. As you might have seen in the previous project, [Building a Neuron in Python](https://patchyst.github.io/My_First_Machine_Learning_Model/), creating even a single neuron can be a bothersome and complicated task for a beginner. However, libraries such as TensorFlow facilitate the process giving you more room to build more complex models, you'll see why here in a second.

## TensorFlow setup
In a Python IDE(my favorite is pycharm with the anaconda enviroment plugin) import tensorflow as tf. Rarely will you ever see TensorFlow imported as something other than tf unless a specific attribute is being imported.
```python
import tensorflow as tf
```
Unlike many other machine learning modules, TensorFlow can do everything that modules like Numpy and Matplotlib can do built into it. This tight integration rids us of many type errors since we'll being using TensorFlow variables along side TensorFlow methods. For example, instead of using a Numpy array we can use tensors which are a special type of multidimensional array unique to TensorFlow. Since machine learning uses massive datasets and plots them on a graph sometimes the graphs are not fully cleared. Luck for us TensorFlow has a built in funciton for wiping all data that may be crowding our graph:
```python
import tensorflow as tf
tf.reset_default_graph()
```
