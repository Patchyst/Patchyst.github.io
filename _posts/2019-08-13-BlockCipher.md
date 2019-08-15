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
