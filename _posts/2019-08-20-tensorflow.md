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
Unlike many other machine learning modules, TensorFlow can do everything that modules like Numpy and Matplotlib can do built into it. This tight integration rids us of many type errors since we'll being using TensorFlow variables along side TensorFlow methods. For example, instead of using a Numpy array we can use tensors which are a special type of multidimensional array unique to TensorFlow, tensors can be a single value, a list, or a multidimensional list of values. Since machine learning uses massive datasets and plots them on a graph sometimes the graphs are not fully cleared. Lucky for us, TensorFlow has a built in funciton for wiping all data that may be crowding our graph:
```python
import tensorflow as tf
tf.reset_default_graph()
```
Using this function should be the first thing you do before every model. Now time to familiarize you with some of the basic functionalities in TensorFlow. To begin, you can create a constant tensor variable using tf.variable_type(value, dtype = datatype). For this example we'll create a constant to keep it simple:
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)
```
The **constant** part is specifying the type of variable we want to create which in our case is a constant, **50.0** is the variable value, and **tf.float32** is specifying that our value(s)(50.0) equals a float data type. You'll probably see tf.float32 as the data type for almost every TensorFlow variable. Before we can do any operations to our constant or to anything for that matter, we have to start a TensorFlow sessions.
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)

with tf.Session() as sess:
```
This begins our sessions under the name of sess. I renamed it to sess so we can run operations easily in the session. To show you lets add 20.0 to our constant:
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)

with tf.Session() as sess:
    print(sess.run(number + 20.0))
```
You might see a few warnings that look like errors, don't worry, as long as at the end you see an output of "70.0".
## *Passing in Input Data*
When passing input data into a computational graph, TensorFlow uses placeholders to take in this data. By adjusting the parameters of the placeholder nodes you can change the type of input data that is fed into the graph or network. Every placeholder node has some sort of parameters for shape, shape is the number of dimensions and elements a tensor has. For example, [1,2,3] is one dimension with 3 elements(3), [[1,2],[3,4]] is 2 dimensions with 2 elements per dimension(2,2). Lets create a variable for placeholder input data in the same format that we made the constant variable:
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)
input_node = tf.placeholder(dtype=tf.float32, shape=None)

with tf.Session() as sess:
    print(sess.run(number + 20.0))
```
