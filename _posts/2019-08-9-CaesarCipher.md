---
title: "ASCII Caesar Cipher"
date: 2019-08-9
tags: [Basic Projects, Python]
header:
  image: "images/caeser.jpg"
excerpt: "A Caeser Cipher made using ASCII values"
---

# What is a Caeser cipher?
As you've probably guessed it has something to do with Julius Caesar. While the Caesar Cipher probably wasn't invented by Caeser himself, history suggests he used it frequently. Whenever Caeser had anything confidential to say, he would write in a shift cipher or what we now call the Caeser Cipher. The Caesar Cipher or shift cipher is one of the oldest known ciphers in cryptography. As of now, it's pretty much useless with only 26 possible cipher possibilities it's vulnerable to even a brute force attack done by hand. However, at a time when most people were illiterate Caeser, it was probably pretty securee.

## Advantages of using ASCII values
As I said before, a regular old shift cipher regulates you to just 26 possibilities, using ASCII opens up a world of mapping possibilities that weren't there before. If you aren't already familiar with ASCII values, I suggest you [Click Here](https://patchyst.github.io/indexASCII/) to fully understand. In fact, if you research how to make a Caesar Cipher in Python you'll probably get at least 5-15 lines of code. I can show you how to make an even more secure cipher in just four lines of code!

## making the ASCII Shift cipher
To begin, we have to make two variables one for the key and one for the message. For this project I will be using input variables so I can change my message and key whenever I feel like doing so.
```python
message = input("Enter the message you want to be encoded: ")
x = int(input("Enter a shift key: "))
```
Now we will create a for loop that iterates through the message variable and enciphers each letter one by one and outputs them.
```python
message = input("Enter the message you want to be encoded: ")
x = int(input("Enter a shift key: "))
for i in message:
  print(chr(ord(i)+x), end = "")
```
Inside the for loop the index value of the character going through the loop has the shift key added to it then the chr() function finds the corresponding character to shifted number. Lastly, the end = "" makes it so each of the letter prints on the same line. Play around entering messages you want to be enciphered and you will get all kinds of random letters and symbols that would be extremely hard to decode by hand without the key.


# Now What?
If you're still interested in encryption I suggest you check out the [XOR Stream Cipher](https://patchyst.github.io/XORstream/) or the [Hexadecimal Block Cipher](https://patchyst.github.io/BlockCipher/) posts I made!

### Issues with code?
See the fully working gist code [here](https://gist.github.com/Patchyst/06006ea382d27e26b0be4abaf7246948)
