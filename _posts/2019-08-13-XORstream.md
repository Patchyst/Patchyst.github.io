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
Pretty soon we are going to use a for loop to iterate through our code list and append the results to another list of integers which will be our encoded binary, so create an empty list variable along with the code and key variable.
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
Create a variable called cipher_bit that uses the XOR operator on each of the corresponding index values for code_ints and key_ints.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_integers = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
```
Finally we will convert our encoded message into a string.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_integers = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher = "".join(str(x) for x in cipher_ints)
```
If you would like to watch the encryption process as your code runs copy the cipher variable code text and throw it inside a print statement.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_integers = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher = "".join(str(x) for x in cipher_ints)
  print("".join(str(x) for x in cipher_ints))
```
