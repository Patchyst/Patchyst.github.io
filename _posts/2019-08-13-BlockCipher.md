---
title: "Hexadecimal Block Cipher Encryption"
date: 2019-08-13
tags: [Advanced Projects, Encryption, Binary and Hexadecimal, Python, Cyber Security]
header:
  image: "images/encryption_ban.jpg"
excerpt: ""
---
Before starting on this project you should have a solid understanding of index values and hexadecimal. If not you can check out these two posts I wrote on both topics: [Index Values](https://patchyst.github.io/indexASCII/), [Hexadecimal Numbers](https://patchyst.github.io/hexadecimalandcharactercodes/)
# The Block Cipher
As the name suggest the block breaks messages into blocks of data each made up of a couple bytes of data in hexadecimal form. Unlike a [Stream Cipher](https://patchyst.github.io/indexASCII/) a block cipher encrypts blocks of data rather than individual bits of data.
## Separating the message into blocks
Each block in this project will be separated into 3 - 4 bytes of data or 24 - 32 bits of data.
To begin, define a function that takes in the message and block size as arguments. This function will be used to separate the message into chunks of data:
```python
def chunk_message(message, block_data = 4):
```
Now create an empty list for the "chunked" message and a variable for the block
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block = 0
```
figure out the number of blocks in the message:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block = 0
  block_count = len(message) // block_data + 1
```
You may be wondering why there is a + 1 at the end. This is to ensure the last block is the correct size, this means that the last block will be spaced with a few extra bits.
Next create a for loop that iterates through our message:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block = 0
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
```
If you read the post I made on [binary numbers](https://patchyst.github.io/binaryintro/) you may be familiar with bit shifting in Python. In the for loop shift the block variable 1 byte or 8 bits to the right:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block = 0
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = block << 8
```
If the character is still less than the message's length use the ord() function on the character to transform it into it's integer value and add it to the block:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block = 0
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = block << 8'

    if character < len(message):
     block += ord(message[character])
 else:
     block += 0
```
