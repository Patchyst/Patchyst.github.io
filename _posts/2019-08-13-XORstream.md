---
title: "XOR Stream Cipher"
date: 2019-08-13
tags: [Encryption, Binary and Hexadecimal, Python, Cyber Security]
header:
  image: "images/cyber.jpg"
excerpt: "Create a Python Program that utilizes Binary Numbers and a XOR gate to create a secure code exchange"
---
Before beginning this project you should have a good grasp on binary and logic gates, if not than it might be helpful to check out [this post](https://patchyst.github.io/binaryintro/) I wrote on binary numbers and logic gates as it serves as a good prerequisite.
## Creating the Cipher
To begin, we will create two strings one for the key, and one for the binary message. It's critical that the message and binary key be the same length of bits. For this project I will be using a set variable, but if you prefer you can transform them into an input, as long as the key and message are the same bit length. This Program works with as many bytes of data as you want. Now lets set the variables:
```python
code = "1001111010100001"
key = "0001110101010101"
```
Now we convert our strings to a list of integers using a for loop.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
```
Pretty soon we are going to use a for loop to iterate through our strings and append the results to a list of integers, so create an empty list variable along with the code and key variable.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []
```
Now we will create a for loop that iterates through the list for the length of our code.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_integers = []
for i in range(len(code_ints)):
```
