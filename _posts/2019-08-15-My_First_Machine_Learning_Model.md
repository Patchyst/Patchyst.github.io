---
title: "Building a Neuron in Python (unfinished)"
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
In terms of Machine Learning a neuron can be broken to a simple algebraic equation, slope-intercept form (y = mx + b). x as the input data, m as the weights, b as the bias, y as the output. **Inputs** are a set of values that represents data from a data set or another neuron, values passed in through an input serve to adjust and fine tune the weights of a neuron. **weights** control the shape of the linear regression graph, in a neural network all the "nodes" are connected via weights (e.g. output of one neuron connected to another neuron's input). When a neural network is created the weights are randomly initialized with a value in between -1 and 1. As the machine learning model continues to run, loss is calculated and the weights are fine tuned and adjusted to favor certain outputs. With that in mind a weight is the strength of connection between nodes. A negative weight decreases the favorability of an output while a large weight will be a favored output. Throughout the training process these weights will be fine tuned so that the proper conclusion is reached for every output. In short you reduce the weights of the incorrect or unfavorable outputs and increase the weights of favorable or correct outputs. **bias** helps adjust the output in correspondence with the given data, but having a high bias is the result misinterpreting the underlying goal of a dataset. Unfortunately, linear regression machine learning models are examples of a parametric algorithm meaning it's pretty strict about changing it's parameters. This means that they usually have a  high bias making them bad for complex data sets. However, for simple datasets linear regression works as intended.

## Activation Functions:
An Activation or Transfer function is an essential part of every neuron, it takes the output from the previous neuron and sees if the value meets the boundaries of the preferred value. For example, if the output doesn't meet a required threshold then the neuron is not activated and the neuron becomes 0. Activation functions withhold useless outputs and assist in weight adjustment. To put it simply the activation function allows the neural network to find the error in its equation.

### *Common Activation Functions*

![Activation Function](/images/activationfunction.jpg){:class="img-responsive"}

## Forward Propagation
Forward Propagation, also known as the training step is the process of using the y=mx+b form before the activation function, then comparing the output with the desired output and getting the error.

## Different Data Set types
* Training Data: The data that the model uses to learn, improve, and "train" from
* validation Data: An unbiased data set used to fine tune the model's hyperparameters
* Test Data: Used after all the training and validation data has been used. As the name suggests it is used to "test" the model's ability.

# **Building the Neuron**
Since creating a Neuron can be confusing lets it down into steps:
* 1- Take in the training data as an input
* 2- Neuron processes the data and produces a loss
* 3- Adjust the weights based off the loss
* 4- Repeat steps 1-3 until the expected output is met

## *Modules being used in this project*
### Numpy
Numpy is a useful module to use in any Machine Learning Project because it can make massive multidimensional arrays to serve as data sets which can be changed with ease.
### Matplotlib
Matplotlib is being used because it allows us to easily graph large data sets and outputs.
## Open a Python IDE...
Open a Python IDE and import numpy, random from numpy, and Matplotlib.pyplot. Make sure you've pip installed these modules and are using an IDE that supports these modules.
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt
```
Create a parent class for the neuron:
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
```
Next we use random.seed() to initialize a random weight, then create the random numbers between -1 and 1 for the weights array shape ([1,1]). Since the random generator doesn't generate numbers between -1 and 1, we have to multiply the number generated between 0 and 1 and subtract by 1:
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
        rand.seed(1)
        self.weights = 2 * rand.random((1, 1)) - 1
```
Next add the activation function, this will turn our linear data into non-linear data. Don't be intimidated by any of the math for the activation function because most data scientists try out every activation function to see which one outputs the highest accuracy. You could do all the math for the activation functions before making the model, but it's much easier to go by trial and error and it's common practice. For this project we'll be using the TanH activation function, we don't have to define it because it's built into Numpy. However, you do have to create a function that calls the TanH function and returns the value.
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
        rand.seed(1)
        self.weights = 2 * rand.random((1, 1)) - 1

    def activation_function(self, x):
        return 1 - np.tanh(x)**2
```
Now that we've added the weights as attributes to our neuron, and declared an activation function, lets begin the training phase, also known as forward Propagation. Going back to the y = mx + b format, you see that the first thing we must do is multiply the inputs by the weights. This can be done by using another built in numpy function called "dot" that multiply matrices together. Create a another function called training_step that returns the dot product of our 2D arrays and sends it through our activation function:
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
        rand.seed(1)
        self.weights = 2 * rand.random((1, 1)) - 1

    def activation_function(self, x):
        return 1 - np.tanh(x)**2

    def training_step(self, x):
        dot_value = np.dot(x, self.weights)
        return np.tanh(dot_value)
```
Now that we've created methods for the activation function and the training step we can begin creating the learning process for the neuron. Declare a method called learn that takes in four parameters, self, training_duration, train_input, and train_output. Whatever we input for the **training_duration** variable will determine how much training the neuron goes through. The **train_input** is the input data for the training data. Since this model uses super visional learning we're giving it the desired output (**train_output**) so it can compare it with it's own output, find the error, and adjust the weights. Inside the learn method run a for loop that "trains" the model by the training_duration variable:
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
        rand.seed(1)
        self.weights = 2 * rand.random((1, 1)) - 1

    def activation_function(self, x):
        return 1 - np.tanh(x)**2

    def training_step(self, x):
        dot_value = np.dot(x, self.weights)
        return np.tanh(dot_value)

    def learn(self, training_duration, train_input, train_output):
        for i in range(training_duration):
```
Inside declare a variable called "output" that returns the result of the training_Step method, and find the error by subtracting the train_output variable by the output variable and then adjusting the self.weights:
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
        rand.seed(1)
        self.weights = 2 * rand.random((1, 1)) - 1

    def activation_function(self, x):
        return 1 - np.tanh(x)**2

    def training_step(self, x):
        dot_value = np.dot(x, self.weights)
        return np.tanh(dot_value)

    def learn(self, training_duration, train_input, train_output):
        for i in range(training_duration):
            output = self.training_step(train_input)
            error = train_output - output
            self.weights += weight_modification
```
Now the hard part, creating a variable for the number the weights need to be adjusted by. We achieve this by taking the dot product of the input data transposed and the error multiplied by the activation function of the "output". Transposing an array just means turning rows of data into columns of data:
```python
import numpy as np
import numpy.random as rand
import matplotlib.pyplot as plt


class Neuron:
    def __init__(self):
        rand.seed(1)
        self.weights = 2 * rand.random((1, 1)) - 1

    def activation_function(self, x):
        return 1 - np.tanh(x)**2

    def training_step(self, x):
        dot_value = np.dot(x, self.weights)
        return np.tanh(dot_value)

    def learn(self, training_duration, train_input, train_output):
        for i in range(training_duration):
            output = self.training_step(train_input)
            error = train_output - output
            weight_modification = np.dot(train_input.T, (error * self.activation_function(output)))
            self.weights += weight_modification

```
Now our neuron is ready to be trained with sample data, let's get into the process of doing that..

# Creating data to teach our model by:
Outside the neuron class create a linear function that the neuron is going to learn:
```python
def linear_function(x):
    return 2 * x
```
Now define the input and output data using for loops:
```python
def linear_function(x):
    return 2 * x


input_data = [n/100 for n in range(300)]
output_data = [linear_function(n/100) for n in range(300)]

```
The neuron will plot the input data and compare it with the output, adjust the weights, and keep going until it has figured out the right linear function. Next convert the input and output data to numpy arrays.
```python
def linear_function(x):
    return 2 * x


input_data = [n/100 for n in range(300)]
output_data = [linear_function(n/100) for n in range(300)]

input_data = np.asarray([input_data])/100
output_data = np.asarray([output_data])/100

```
Create an object for your neuron class:
```python
def linear_function(x):
    return 2 * x


input_data = [n/100 for n in range(300)]
output_data = [linear_function(n/100) for n in range(300)]

input_data = np.asarray([input_data])/100
output_data = np.asarray([output_data])/100

neuron = Neuron()
```
Reshape the input_data array into 2D form and transpose the output_data just like what we did in the learn method:
```python
def linear_function(x):
    return 2 * x


input_data = [n/100 for n in range(300)]
output_data = [linear_function(n/100) for n in range(300)]

input_data = np.asarray([input_data])/100
output_data = np.asarray([output_data])/100

neuron = Neuron()

input_data = input_data.reshape(300, 1)
output_data = output_data.T

```
Lastly, we must make a variable for the plotted output data using the same equation. We can do this by creating an empty list to append the points to:
```python
def linear_function(x):
    return 2 * x


input_data = [n/100 for n in range(300)]
output_data = [linear_function(n/100) for n in range(300)]

input_data = np.asarray([input_data])/100
output_data = np.asarray([output_data])/100

neuron = Neuron()

input_data = input_data.reshape(300, 1)
output_data = output_data.T

y_plotted_data = []
for i in range(300):
    y_plotted_data.append(linear_function(i/100)+rand.randint(1, 100)/50)

```


## Training the Neuron:
To train the neuron we just reference the object along with the learn method we created for training it.
```python
neuron.learn(20000, input_data, output_data)

```
As you can see we are entering the parameters that we initialized while making the function, the neuron will train for the duration of 20,000 and we are using the input_data as the input and output_data as the desired to output that the neuron can compare it's own output with and adjust it's weights based off of. However, making the neuron "learn" is just half the fun we want to watch it's progress. create a variable that has the weights that the neuron is adjusting as it learns:
```python
neuron.learn(20000, input_data, output_data)
weight_constant = neuron.weights[0][0]
```
Now create an empty list that we will append weight constants to and plot to watch the gradual learning of the proper linear function:
```python
neuron.learn(20000, input_data, output_data)
weight_constant = neuron.weights[0][0]
learning_data = []

```
use a for loop to append the adjusting of weights to the learning_data:
```python
neuron.learn(20000, input_data, output_data)
weight_constant = neuron.weights[0][0]
learning_data = []

for n in input_data:
    learning_data.append(n*100*weight_constant)
```
And Finally we use the matplotlib built in functions plt.plot and plt.show to see our results:
```python
neuron.learn(20000, input_data, output_data)
weight_constant = neuron.weights[0][0]
learning_data = []

for n in input_data:
    learning_data.append(n*100*weight_constant)

plt.plot(y_plotted_data, "bo")
plt.plot(learning_data, "r-")
plt.show()
```
### *Output*
You Should see the image:

![Graph](/images/graph.jpg){:class="img-responsive"}

As you can see neuron has created a line to match the linear function used for the input.

# What Next?
