---
title: "Hexadecimal Block Cipher Encryption"
date: 2019-08-12
tags: [Advanced Projects, Python, Cyber Security]
header:
  image: "images/encryption_ban.jpg"
excerpt: "A secure Block Cipher encryption made using hexadecimal and binary"
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
Now create an empty list for the "chunked" message, and a block variable:
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
If you read the post I made on [binary numbers](https://patchyst.github.io/binaryintro/) you may be familiar with bit shifting in Python. In the for loop shift the block variable 1 byte or 8 bits to the left to make space for the next byte:
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
  block = 0
  block_count = len(message) // block_data + 1
  for character in range(block_count * block_data):
    block = block << 8

    if character < len(message):
     block += ord(message[character])
    else:
     block += 0

    if block.bit_length() > (block_data -1) * 8:
      message_chunked.append(block)
      block = 0
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
      block = 0
  return message_chunked
```
What we've done here is preprocesses the message by breaking it into chunks of numbers making it easier for the encryption function.

## Shifting the Blocks
Block Ciphers shift bits in a way that effect the entire block of data. All the bits may makeup different characters, but they can all be shifted as if they were one binary number adding more ways to concatenate the data. Create a new function below the others to apply the shifts with the arguments for the chunked message, shift key and block size:
```python
def apply_shift(message_chunked, key, block_data = 4):
```
create an empty list for the encrypted message and set a maximum block size
```python
def apply_shift(message_chunked, key, block_data = 4):
  encrypted_message = []
  max_bit = block_data * 8
```
As usual create a for loop that iterates through the chunked messages and set the block variable
```python
def apply_shift(message_chunked, key, block_data = 4):
  encrypted_message = []
  max_bit = block_data * 8
  for n in range(len(message_chunked)):
    block = message_chunked[n]
```
We will now begin shifting the bits, but we first must make a variable that carries over the bits so that they are not lost when they're being shifted. For example, if you have one byte of data and you shift it five places to the left then in the new byte of data the three bits that were effectively "moved" out of the byte are now the first three bits at the beginning of the shifted byte.
Example =
```python
010010111
# shifted to the left by five with the carry
010111010
```
With that in mind create a variable that will accomplish that and shift it to the left
```python
def apply_shift(message_chunked, key, block_data = 4):
  encrypted_message = []
  max_bit = block_data * 8
  for n in range(len(message_chunked)):
    block = message_chunked[n]
    carry = block % (2**key)
     carry = carry << (max_bit - key)
```
Ok, so the math might look confusing at first, but if you take a second to break it down it really isn't. You're taking the block and dividing it by 2 to the power of the key. So going back to the example from earlier, if you plug in the key and block size you get this equation: (8 % 2**5). Well that isn't to bad at all and if you do the math the answer is 3 which if you remember was the number of bits shifted to the beginning of the shifted byte.
Now set the encrypted character value by shifting it to the right and append it to the encrypted_message list. Finally return the encrypted_message.
```python
def apply_shift(message_chunked, key, block_data = 4):
  encrypted_message = []
  max_bit = block_data * 8
  for n in range(len(message_chunked)):
    block = message_chunked[n]
    carry = block % (2**key)
    carry = carry << (max_bit - key)  
    encrypted_character = (block >> key) + carry
    encrypted_message.append(encrypted_character)
  return encrypted_message    
```

## Converting the encrypted message back into a string
Since our encrypted message is currently an integer, it would be helpful to have a function that converts it back into a string. Below the previous function create a new function with arguments for the message_chunked and block size:
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
      byte = (block >> (8 * (block_data - 1 - x))) % 2**8
```
Use the chr() function to convert the integer into it's corresponding character and append it to the message string, and as usual return the message outside of all loops
```python
def string_message(message_chunked, block_data = 4):
  message = ""
  for i in range(len(message_chunked)):
    block = message_chunked[i]
    for x in range(block_data):
      byte = (block >> (8 * (block_data - 1 - x))) % 2**8
      message += chr(byte)
  return message
```

## Running the Program
To begin, create a plaintext variable and a key variable
```python
unencrypted_text = "Hello World"
key = 7
```
Now turn it into blocks and apply the shift
```python
unencrypted_text = "Hello World"
key = 7
block_list = chunk_message(unencrypted_text)
encrypted_list = apply_shift(block_list)
```
Lastly turn the encrypted_list into a string to see the encrypted string
```python
unencrypted_text = "Hello World!"
key = 7
block_list = chunk_message(unencrypted_text)
encrypted_list = apply_shift(block_list, key)
encrypted_string = string_message(encrypted_list)
print(encrypted_string)
```
If you used the same key and unencrypted text as me you should get the output:
```python
ØÊØÞÞ@®BäØÈ
```
# Code Not working?
A few things may be the issue, if you forget to enter the smallest detail or put something inside of a loop when it doesn't belong, the whole code will break. (I learned this the hard way). If you copy and pasted directly from this webpage the difference in indentation may lead to indentation inconsistencies so be sure to check for that. Lastly, I'm going to be linking the working gist page with the full working code ---> [here](https://gist.github.com/Patchyst/88b544098522ff6c742d6811e3c9bcce) <--- So check that out if you want to debug your own.
