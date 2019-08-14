---
title: "Hexadecimal and Character Codes"
date: 2019-08-10
tags: [Binary and Hexadecimal]
header:
  image: "images/hex_two.jpg"
excerpt: "Learn the fundamentals of hexadecimal while preparing to make a hexadecimal encryption(Block Cipher)"
---
If you've ever used [binary numbers](https://patchyst.github.io/binaryintro/) you may recognize the base 2 system, right after binary there is hexadecimal which uses the base 16 system. The hexadecimal alphabet only consists of 16 characters, 1 - 9 after 9, numbers become letters ranging from A to F. Converting hexadecimal to decimal form would look like this:

![hexadecimal-conversion](/images/base_hex.jpg){:class="img-responsive"}

Similar to how python uses 0b as a prefix for Binary numbers, you would you use 0X as a prefix before any hexadecimal numbers. In a python IDE create a variable using hexadecimal notation
```python
A = 0X3e
```
Just like the bin() function, Python uses hex() to print hexadecimal Numbers
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
Well, the answer is quite simple. 8 bits of binary can be represented using two hexadecimal numbers. This means hexadecimal can be used to track massive codes of binary data. For example, 0x8240a79c is much easier to read when compared to 0b10000010010000001010011110011100.

# Character codes
You will most likely encounter hexadecimal in character codes. Character codes are part of [Unicode](https://patchyst.github.io/binaryintro/) which is an international encoding standard for all text characters agreed upon by everyone in the computer industry. Character codes are found in everything ranging from phonetic scripts to emojis. Hexadecimal is behind every character on your computer screen. In case your still confused Python has a few built in functions to help display this. In a python IDE create a list of two character hexadecimal numbers, with an empty string variable.
```python
hex_num = [0X77, 0XA1, 0X44, 0X62, 0X32]
translated_hex = ""
```
create a for loop that iterates through the hex_num variable and translates them into text
```python
hex_num = [0X77, 0XA1, 0X44, 0X62, 0X32]
translated_hex = ""
for x in hex_num:
```
Use the built in chr() method to translate the hexadecimal and print it
```python
hex_num = [0X77, 0XA1, 0X44, 0X62, 0X32]
translated_hex = ""
for x in hex_num:
  translated_hex += chr(x)
print(translated_hex)
```
assuming you used the same variable values as me you should get the output
```python
w¡Db2
```
You could also find a the hexadecimal values of these characters by using the ord() function to turn them into [ASCII](https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html) values and then turn this ASCII values into hexadecimal.
```python
hex_num = [0X77, 0XA1, 0X44, 0X62, 0X32]
translated_hex = ""
for x in hex_num:
  translated_hex += chr(x)
print(translated_hex)
#convert back to hexadecimal values
for i in translated_hex:
  a = ord(i)
  converted_hex = hex(a)
  print(converted_hex)
```
assuming your code and variables are the same as mine the second for loop should output:
```python
119
0x77
161
0xa1
68
0x44
98
0x62
50
0x32
```
As you can see the for loop outputs the ASCII value of the translated_hex then turns that number back to it's corresponding hexadecimal.

## Recap:
Hexadecimal is behind nearly every text, character, and even line on your screen, while it has many uses I won't be going into much detail on them other than how to make a Block Cipher using hexadecimal.

# Now What?
I know, I know, the hexadecimal section was pretty short compared to the binary section. However, now we can move on to make a hexadecimal encryption! To begin on the Block Cipher click here, or navigate to it via the projects page.
