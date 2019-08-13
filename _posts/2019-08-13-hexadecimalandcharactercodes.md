---
title: "Hexadecimal and Character Codes"
date: 2019-08-10
tags: [Binary and Hexadecimal]
header:
  image: "images/hex_two.jpg"
excerpt: ""
---
If you've ever used [binary numbers](https://patchyst.github.io/binaryintro/) you may recognize the base 2 system, right after binary there is Hexadecimal which uses the base 16 system. The Hexadecimal alphabet only consists of 16 characters, 1 - 9 after 9, numbers become letters ranging from A to F. Converting Hexadecimal to decimal form would look like this:

![hexadecimal-conversion](/images/base_hex.jpg){:class="img-responsive"}

Similar to how python uses 0b as a prefix for Binary numbers, you would you use 0X as a prefix before any Hexadecimal numbers. In a python IDE create a variable using hexadecimal notation
```python
A = 0X3e
```
Just like the bin() function, Python uses hex() to print Hexadecimal Numbers
```python
A = 0X3e
B = 34
print(A)
print(hex(A))
#print B in hexadecimal
print(hex(B))
#print A in binary
print(bin(A))
```
If you used the same variables as me you should get the output:
```python
62
0x3e
0x22
0b111110
```
## Why Use Hexadecimal?
Well, the answer is quite simple. 8 bits of binary can be represented using two hexadecimal numbers. This means hexadecimal can be used to track bytes of binary data.
