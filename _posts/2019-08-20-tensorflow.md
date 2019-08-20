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
Setting the shape parameter equal to None means that the node will take in any input regardless of the shape. To test out the input node, lets multiply whatever passes through it by 2:
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)
input_node = tf.placeholder(dtype=tf.float32, shape=None)

multiply = input_node * 2

with tf.Session() as sess:
    print(sess.run(number + 20.0))
```
If you try to run the multiply operation right now you would probably get an error because we haven't passed any data into the input node. We pass data into the input node using the feed_dict parameter:
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)
input_node = tf.placeholder(dtype=tf.float32, shape=None)

multiply = input_node * 2

with tf.Session() as sess:
    print(sess.run(number + 20.0))
    print(sess.run(multiply, feed_dict={input_node: 45.0}))
```
As you can see we're feeding 45 into the input_node and multipying it. Since we specified the input shape as none it can take any shape we pass into it.
```python
import tensorflow as tf
tf.reset_default_graph()
number = tf.constant(50.0, dtype=tf.float32)
input_node = tf.placeholder(dtype=tf.float32, shape=None)

multiply = input_node * 2

with tf.Session() as sess:
    print(sess.run(number + 20.0))
    print(sess.run(multiply, feed_dict={input_node: 45.0}))
    print(sess.run(multiply, feed_dict={input_node: [[3, 3], [4, 4], [5, 5]]}))
```
If you passed in the same (3,3) shape as me you should have received the output:
```python
[[ 6.  6.]
 [ 8.  8.]
 [10. 10.]]
```
Every element was multiplied by 2. Having the ability to change massive data sets is a crucial part of Machine Learning.
## Making the Machine Learning Model:
For this Project the neural network will learn the linear function for a a given set of data points. Create a new file or clear your IDE workspace, then create two placeholders for the input and expected output:
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
```
Since the model is guessing the equation for the line the slope and y intercept will be frequently changing. With this in mind we'll create a tf.Variable class since it can be initialized with a starting value and it's properties can be easily altered by the model.
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
slope = tf.Variable(5.0, dtype=tf.float32)
y_intercept = tf.Variable(1.0, dtype=tf.float32)
```
The 5.0 and 1.0 are the starting values and they will be adjusted as the model "learns". Since we are using a linear regression model we will use y = mx +b format to calculate the models guess:
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
slope = tf.Variable(5.0, dtype=tf.float32)
y_intercept = tf.Variable(1.0, dtype=tf.float32)
# y = mx + b
conclusion_operation = slope * input_node + y_intercept
```
In order for the model to have pinpoint accuracy we need it to be able to compare it's output with the expected output, find the difference, and adjust it's weights based on the difference. Yes, I'm talking about error, however, this time we'll be using a loss function. To put it simply (and I mean grossly simple), only using error for backpropagation when you get more complex models is not good enough, loss is a way of "mapping" the error data into a real number that the model seeks to lower. Essentially the neural networks goal is to reduce the loss function beyond a threshold or eradicate it completely, it does this by learning from how high or low the loss is then using the process of backpropagation to adjust it's weights in correspondence with whatever is causing the "high" loss. There are a few ways to go about doing this since there are many different loss functions out there, all of it just depends on the model and what type of data you're passing in. Our model is fairly simple so we're going to use a common loss function which involves squaring the error of the values and then finding the mean. TensorFlow has functions for squaring and taking the mean of error data built in to it:
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
slope = tf.Variable(5.0, dtype=tf.float32)
y_intercept = tf.Variable(1.0, dtype=tf.float32)
# y = mx + b
conclusion_operation = slope * input_node + y_intercept
error_squared = tf.square(conclusion_operation - output_node)
loss = tf.reduce_mean(error_squared)
```
### *Running the Session*
Running a session with Variable types is pretty much the same as running a session with placeholder and constant types except we need to run an init operation to initialize to variables. Create a variable assigned to the global variable initializer. I used init short for initializer so it's easier to call when running the session.
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
slope = tf.Variable(5.0, dtype=tf.float32)
y_intercept = tf.Variable(1.0, dtype=tf.float32)
conclusion_operation = slope * input_node + y_intercept
error_squared = tf.square(conclusion_operation - output_node)
loss = tf.reduce_mean(error_squared)
init = tf.global_variables_initializer()
```
Start running a TensorFlow Session just as we did before and run the init function inside of it:
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
slope = tf.Variable(5.0, dtype=tf.float32)
y_intercept = tf.Variable(1.0, dtype=tf.float32)
conclusion_operation = slope * input_node + y_intercept
error_squared = tf.square(conclusion_operation - output_node)
loss = tf.reduce_mean(error_squared)
init = tf.global_variables_initializer()


with tf.Session() as sess:
    sess.run(init)
```
Outside of the Session create two sets for the x and y values to serve as input data and output data:
```python
import tensorflow as tf
tf.reset_default_graph()
input_node = tf.placeholder(dtype=tf.float32, shape=None)
output_node = tf.placeholder(dtype=tf.float32, shape=None)
slope = tf.Variable(5.0, dtype=tf.float32)
y_intercept = tf.Variable(1.0, dtype=tf.float32)
conclusion_operation = slope * input_node + y_intercept
error_squared = tf.square(conclusion_operation - output_node)
loss = tf.reduce_mean(error_squared)
init = tf.global_variables_initializer()

x_values = [2, 4, 6, 8, 10]
y_values = [1, 3, 5, 7, 9]


with tf.Session() as sess:
    sess.run(init)
```
