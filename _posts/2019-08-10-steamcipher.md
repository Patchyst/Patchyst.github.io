---
title: "(XOR) Stream Cipher"
date: 2019-08-10
tags: [Encryption, Binary, Cyber Security, Python]
header:
  image: "images/binarybannerone.jpg"
excerpt: "Learn all about Binary Numbers while making a secure Stream Cipher that utilizes a XOR gate to create an encrypted code exchange"
---
# Encryption Project: XOR Stream Cipher
  In this project I will be guiding you (the reader) through the process of making a secure binary encryption.
  To some binary numbers may seem shrouded in mystery and secrecy, a classified code that only natural born
  geniuses can understand. However, binary numbers can be boiled to two simple values that even someone with
  zero knowledge of computer hardware and software can understand.
  *if you already have a good idea of what Binary numbers are you can skip the next three sections*


## What are Binary Numbers?
So what is a Binary Number? Well, as I'm sure you've seen before, or guessed by the bi prefix, Binary consists of a 1 or 0, but what does that really *mean?*
A computer, at the most basic level contains a series of on and off switches. 1 representing *on* and 0 representing *off*. You could go a step further and assign
binary numbers to a boolean value True(1) or False(0). Now lets convert a Binary number to our number system. Unlike the base 10 system Binary uses the base 2 system
![binary-conversion](/images/binaryconversion.jpg){:class="img-responsive"}


## Bits and Bytes
Now that you understand that Binary isn't dark magic, lets look into the grouping of Binary.
To keep it short, a bit is a single binary digit, 8 bits makeup a byte. A word on your computer screen is usually 32 bits or 4 bytes of data. Bytes can store data and execute basic instructions. You've probably heard byte before when shopping for electronics, kilobyte, megabyte, gigabyte, terabyte, etc etc..
A kilobyte is 1024 bytes, a megabyte is 1024 kilobytes and a gigabyte 1024 megabytes, you get the point. Now that we've built a solid foundation in Binary lets make the
encryption!


## Logic Gates
OK ok, I know I said we would begin on the XOR stream cipher, but understanding logic gates is kind of crucial if you want to write the encryption. Remember earlier when I assigned binary numbers to a boolean value? Well, that will come in handy now. Just like an if statement in Python logic gates use Boolean Values.
The following are common boolean operators:
* AND, checks if both statements are True
* OR, check if at least one of the statements are True
* NOT, changes the boolean values of a statement, true to false or false to true
The term "logic gate" originates from how electronic circuits handle booleans, on(true) off(false).
### And Gates
And gates take in two bits as an input and produce a single bit as an output. If both input bits are a 1(true) then the output bit is a 1(true).
Just like the And operator used in regular Python if both conditions are True the output is True, if one of the conditions in false the output is False. On paper an and logic gate is often written in a D.
![and-gate](/images/andgate.jpg){:class="img-responsive"}
### Or Gates
Or gates just like And gates take in two bits as an input and produce 1 bit as an output. However, there is one key difference, I like to think of an Or gate as the opposite of an and gate. In an Or gate if any inputs are a 1(true) then the output will be 1(true), but if both input are 0(false) then the output with be 0(false). On paper:
![or-gate](/images/orgate.jpg){:class="img-responsive"}
### Not Gates
Unlike the others the Not gate only takes in **one** input and produces just **one** output. Out of all the Logic gates this one is my favorite because of it's simplicity. It takes in one bit and the output is the inverse bit. For example, if you passed in a 1(true) the output would be 0(false). On paper:
![not-gate](/images/notgate.jpg){:class="img-responsive"}
## Using Logic Gates in Python
Now we will see how these logic operators work in a Python IDE
1. Create two variables with different binary numbers using binary notiation (0b)
```python
    A = 0b1110
    B = 0b0101
```
2. Use bit-wise operators that take in the two binary numbers(except for the not gate use one variable) as inputs (& = And gate, | = Or gate, ~ = Not gate)
```python
    A = 0b1110
    B = 0b0101
    X = A & B
    Y = A | B
    Z = ~A
```
3. Use the built in bin() function to print the outputs
```python
    A = 0b1110
    B = 0b0101
    X = A & B
    Y = A | B
    Z = ~A
    print(bin(X))
    print(bin(Y))
    print(bin(Z))
```
