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
## Preprocessing the Message
Each block in this project will be separated into 3 - 4 bytes of data or 24 - 32 bits of data.
To begin, define a function that takes in the message and block size as arguments. This function will be used to separate the message into chunks of data:
```python
def chunk_message(message, block_data = 4):
```
Now create an empty list for the "chunked" message:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
```
figure out the number of blocks in the message:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block_count = len(message) // block_data + 1
```
You may be wondering why there is a + 1 at the end. This is to ensure the last block is the correct size, this means that the last block will be spaced with a few extra bits.
Next create a for loop that iterates through our message with a variable for the block:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = 0
```
If you read the post I made on [binary numbers](https://patchyst.github.io/binaryintro/) you may be familiar with bit shifting in Python. In the for loop shift the block variable 1 byte or 8 bits to the left:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = 0
    block = block << 8
```
If the character is still less than the message's length use the ord() function on the character to transform it into it's integer value and add it to the block:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = 0
    block = block << 8

    if character < len(message):
     block += ord(message[character])
 else:
     block += 0
```
Using the bit_length() function check if the block running through the loop meets the required number of bits/bytes, if it does append it to the list and reset the block variable for the next set of characters:
```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = 0
    block = block << 8

    if character < len(message):
     block += ord(message[character])
    else:
     block += 0

    if block.bit_length() > (block_data -1) * 8:
      message_chunked.append(block)
      block += 0
```
Finally return the message_chunked:

```python
def chunk_message(message, block_data = 4):
  message_chunked = []
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = 0
    block = block << 8

    if character < len(message):
     block += ord(message[character])
    else:
     block += 0

    if block.bit_length() > (block_data -1) * 8:
      message_chunked.append(block)
      block += 0
  return message_chunked
```
What we've done here is preprocesses the message by breaking it into chunks of numbers making it easier for the encryption function.

## Converting the chunked message back into a string
Since our message is currently an integer, it would be helpful to have a function that converts it back into a string. Below the previous function create a new function with arguments for the message_chunked and block size:
```python
def string_message(message_chunked, block_data = 4):

```
Add an empty string variable for the message and a for loop to iterate through the chunked message:
```python
def string_message(message_chunked, block_data = 4):
  message = ""
  for c in range(len(message_chunked)):
```
Create a block variable set to the current integer going through the for loop:
```python
def string_message(message_chunked, block_data = 4):
  message = ""
  for i in range(len(message_chunked)):
    block = message_chunked[i]
```
Create a nested for loop that iterates through the block using the block size:
```python
def string_message(message_chunked, block_data = 4):
  message = ""
  for i in range(len(message_chunked)):
    block = message_chunked[i]
    for x in range(block_data):

```
Since each block is 4 bytes(32 bits) of data, extracting the correct byte takes a bit of math, the first character has to be taken from the first 8 bits so the block is shifted right in steps of 8. Lastly, we use the modulo to remove any unwanted bits. Now enter the following equation into the nested for loop:
```python
def string_message(message_chunked, block_data = 4):
  message = ""
  for i in range(len(message_chunked)):
    block = message_chunked[i]
    for x in range(block_data):
      byte = block >> (8 * (block_data - 1 - x)) % 2**8
```
Use the chr() function to convert the integer into it's corresponding character and append it to the message string, and as usual return the message outside of all loops:
```python
def string_message(message_chunked, block_data = 4):
  message = ""
  for i in range(len(message_chunked)):
    block = message_chunked[i]
    for x in range(block_data):
      byte = block >> (8 * (block_data - 1 - x)) % 2**8
      message.append(chr(byte))
  return message
```
