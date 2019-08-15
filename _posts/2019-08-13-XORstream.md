---
title: "XOR Stream Cipher"
date: 2019-08-13
tags: [Advanced Projects, Encryption, Binary and Hexadecimal, Python, Cyber Security]
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
cipher_ints = []

for i in range(len(code_ints)):
```
Create a variable called cipher_bit that uses the XOR operator on each of the corresponding index values for code_ints and key_ints.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]  
```
Append the cipher bits to the cipher integers list
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher_ints.append(cipher_bit)
```


Finally we will convert our encoded message into a string.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher_ints.append(cipher_bit)
  cipher = "".join(str(x) for x in cipher_ints)
```
(Optional) If you would like to watch the encryption process as your code runs copy the cipher variable code text and throw it inside a print statement.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher_ints.append(cipher_bit)
  cipher = "".join(str(x) for x in cipher_ints)
  print("".join(str(x) for x in cipher_ints))
```
To see the full result simply add a print(cipher) outside the for loop
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher_ints.append(cipher_bit)
  cipher = "".join(str(x) for x in cipher_ints)
  print("".join(str(x) for x in cipher_ints))
print(cipher)
```
(Optional) Ok, well we have a fully encrypted binary number, but it's still technically a string so if you want to do more operations, or add more layers of encryption you would just turn the cipher variable into an integer with a base of 2.
```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher_ints.append(cipher_bit)
  cipher = "".join(str(x) for x in cipher_ints)
  print("".join(str(x) for x in cipher_ints))
print(cipher)
cipher_binary = (int(cipher, base=2))
```
print out the cipher_binary variable and you will get your encrypted binary number in decimal form!

```python
code = "1001111010100001"
key = "0001110101010101"
code_ints = [int(i) for i in str(code)]
key_ints = [int(i) for i in str(key)]
cipher_ints = []

for i in range(len(code_ints)):
  cipher_bit = code_ints[i] ^ key_ints[i]
  cipher_ints.append(cipher_bit)
  cipher = "".join(str(x) for x in cipher_ints)
  print("".join(str(x) for x in cipher_ints))
print(cipher)
cipher_binary = (int(cipher, base=2))
print(cipher_binary)
```
## Why all the conversions between integers, strings, and lists?
Yes, I recognize that this code could be even shorter than it already is, but its important to get into the habit of changing the variable types so you aren't just limited to logic gates and binary encryptions. Now you can go into the code, edit a few variables and add another layer of encryption if you want to.

## So what?
Well, if you haven't already noticed changing anything in the slightest in binary will result in some drastic changes, with all the possible outcomes when using logic gates it's arguably impossible to decrypt unless you were to share your encryption key with someone meaning your encryption is only breakable by human error.
