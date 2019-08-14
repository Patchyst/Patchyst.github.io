---
title: "ASCII Caesar Cipher"
date: 2019-08-9
tags: [Basic Projects, Python, Encryption]
header:
  image: "images/caeser.jpg"
excerpt: "A Caeser Cipher made using ASCII values"
---

# What is a Caeser cipher?
As you've probably guessed it has something to do with Julius Caesar. While the Caesar Cipher probably wasn't invented by Caeser himself, he certainly boosted it's recognition. Whenever Caeser had anything confidential to say he would write in a shift cipher or what we now call the Caeser Cipher. The Caesar Cipher or shift cipher is one of the oldest known ciphers in cryptography. As of now it's pretty much useless with only 26 possible mappings it's vulnerable to even a brute force attack done by hand. However, at a time when most people were illiterate Caeser probably considered his clever little cipher pretty secure. The only issue with a Caeser cipher nowadays is that once someone realizes your using a Caeser Cipher it won't take them long at all to decode your message. In 1883 Auguste Kerkhoff proclaimed in an innovative essay, "The system must not require secrecy and can be stolen by the enemy without causing trouble". At the time I'm sure people thought he was crazy, "How can you make an encryption with so many possibilities that a brute force is impossible?". Well, with the invention of computers we **are** able to make those encryptions, encryptions like the [XOR Stream Cipher](https://patchyst.github.io/XORstream/) or the [Hexadecimal Block Cipher](https://patchyst.github.io/BlockCipher/) are pretty much only broken through human error and social engineering.
# Advantages of using ASCII values for a Shift Cipher instead of the alphabet
As I said before, a regular old shift cipher regulates you to just 26 mapping possibilities, using ASCII opens up a world of mapping possibilities that weren't there before. If you aren't already familiar with ASCII values I suggest you [Click Here](https://patchyst.github.io/indexASCII/) to fully understand. In fact, if you research how to make a Caesar Cipher in Python you'll probably get at least 5-15 lines of code while I can show you how to make an even more secure encryption in just four lines of code!


## making the ASCII Shift cipher
To begin, we have to make two variables one for the key and one for the message. For this project I will be using input variables so I can change my message and key whenever I feel like doing so.
```python
message = input("Enter the message you want to be encoded: ")
x = int(input("Enter a shift key: "))
```
Now we will create a for loop that iterates through the message variable and encrypts each letter one by one and outputs them.
```python
message = input("Enter the message you want to be encoded: ")
x = int(input("Enter a shift key: "))
for i in message:
  print(chr(ord(i)+x), end = "")
```
Inside the for loop the index value of the character going through the loop has the shift key added to it then the chr() function finds the corresponding character to shifted number. Lastly, the end = "" just makes it so each of the letter prints on the same line.
 Now lets test it out! I'll enter "Hello World!" as my message with a shift key of 15 and I get the output:
 **Wt{{~/f~{s0**
Just from looking at that output you can tell that the message we used as an input would be much harder to decrypt than a bunch of letters.

# Now What?
I suggest if you're still interested in encryption check out the [XOR Stream Cipher](https://patchyst.github.io/XORstream/) or the [Hexadecimal Block Cipher](https://patchyst.github.io/BlockCipher/) posts I made!
