---
title: "ASCII and Index Values"
date: 2019-08-9
tags: [Python]
header:
  image: "images/python_index.jpg"
excerpt: "An intro to ASCII values and Index values for beginner Python Programmers"
---
As I was making all the posts with instructions on how to build encryptions I realized that a part of many encryptions involves ASCII values and index values. Even if your new to Python or any programming language for that matter, you may recognize ASCII and index values. With this in mind I decided to make a little refresher page on the basics of ASCII and index values.

## Index values
Whether it be a list, a string, or tuple, every value or character has an index value for its position. For example if you had a list of strings:
```python
my_list = ["F", "A", "Y", "E", "R"]
```
Each character in that list would have a unique index value corresponding with it's position. You can call an index value by using the variable name with the index value in brackets
```python
my_list = ["F", "A", "Y", "E", "R"]
print(my_list[0])
```
The output would be "F" because index values start from 0 then go to 1, 2 ,3.
```python
my_list = ["F", "A", "Y", "E", "R"]
print(my_list[0])
print(my_list[3])
print(my_list[1])
```
The output would be in this order: "F", "E", "A". You can also reference values in a data type using negative index values. -1 would return the last value -2 second to last value and so on.
```python
my_list = ["F", "A", "Y", "E", "R"]
print(my_list[-1])
print(my_list[-2])
```
If you run this program you should see the values "R" and "E" in that order
You can also use a : to print out a group of index values as such:
```python
my_list = ["F", "A", "Y", "E", "R"]
#will print everything out from index value 0 and on
print(my_list[0:])
#prints everything out index value 0-2 but not index value 3
print(my_list[0:3])
#will print everything behind index value 4 but not index value 4
print(my_list[:4])
```
What makes index values useful in encryption is you can use them to rearrange values(e.g. [block cipher](https://patchyst.github.io/BlockCipher/) ) Index values aren't just for Python either, they're universally used throughout all languages and are an essential part of software development.

## ASCII Values
ASCII or American Standard Code for Information Interchange, is an encoding standard for any text or character in electronics. ASCII codes are used in everything from telecommunications to websites. Since computers can't exactly understand letters all the ASCII values are numbers and represent a character. Chart of ASCII values:

![ASCII-Values](/images/ASCII.jpg){:class="img-responsive"}

To get the ASCII values of numbers and characters Python has some neat built in functions. In a Python IDE try out the chr() and ord() functions:
```python
print(ord("a"))
print(chr(97))
```
You should get the output:
```python
97
a
```
the ord() function found the ASCII value for "a" while the chr() function found the letter that 97 was representing. You can use these ASCII values to take numbers from an encryptions and turn them into letters.

#What now?
Well, you can make your very own Caesar Cipher using ASCII values you can check out the instructions on how to make it here.
