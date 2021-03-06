---
title: "Patchy Hash Cracker"
date: 2020-05-15
tags: [Advanced Projects, python, bash]
header:
  image: "images/patchyhash.gif"
excerpt: "Patchy Pack's hash cracker usage"
---
As of now, hashing algorithms are broken using a simple brute force attack, but a hybrid and mask attack are also being developed.
## Target hash format:
Patchyhash supports a variety of hashing algorithms such as md5, sha512, sha256, sha224, sha1, sha384, and DES. Target password hashes must be stored in a file. For this example I'll be using a couple passwords hashed in sha256 format, a cryptographic function part of the sha2 set designed by the United States National Security Agency in 2001. The most reliable way to add hashes to a file is to echo the output to a file. Im going to decrypt the password, i2CDGeda which equals 9aa2bf82ba045569731de71a5c95463b9297345ea5c6f6f56d29a5e9b6857f47 when sent through the sha256 cryptographic function.
*-n sends the text to a file without appending a new line. Typically a good idea when using any hash cracking program as even something as small as a newline can drastically change the hash*
```python
echo -n "9aa2bf82ba045569731de71a5c95463b9297345ea5c6f6f56d29a5e9b6857f47" > shapass.txt
```
The only two required arguments is the path to the hash file and the path to the wordlist for patchyhash to check against:
```python
patchyhash /root/shapass.txt /root/wordlists/rockyou.txt
```
If you're using Kali Linux wordlists such as rockyou.txt will be stored in us/share/wordlists:
```python
patchyhash /root/shapass.txt /usr/share/wordlists/rockyou.txt
```
If no hashing algorithm is specified then patchyhash will default to md5.
```python
--hash_type
```
or
```python
-ht
```
This will let you specify the sha256 hashing algorithm:
```python
patchyhash /root/shapass.txt /root/wordlists/rockyou.txt --hash_type sha256
```
If you want to view the brute force process:
```python
--view_all
```
or
```python
-va
```
Alright so I want to view the process so our final command will be:
```python
patchyhash /root/shapass.txt /root/wordlists/rockyou.txt --hash_type sha256 -va
```
The output (running on a kali VM):
![hexadecimal-conversion](/images/patchyout.png){:class="img-responsive"}
## DES
DES is a salting hash meaning that additional characters are added to the beginning or end of the hash during the function. For this example, I'll be cracking the hash "hxyoIIVd06sfo". The salt in DES is usually the first two characters so the salt here would be hx. Let's start by echoing hxyoIIVd06sfo to a file.
*Note that > will create a new file, if a file already exists with the same name, > will overwrite it. To add to an existing file use >>*
```python
echo -n "hxyoIIVd06sfo" > DESpass.txt
```
Next we'll tell the program we want to use the DES hashing algorithm and view the brute force process:
*remember that -ht does the same thing has --hash_type*
```python
patchyhash /root/DESpass.txt /root/wordlists/rockyou.txt -ht DES -va
```
**OUTPUT:**
![DES](/images/DESoutput.gif){:class="img-responsive"}
