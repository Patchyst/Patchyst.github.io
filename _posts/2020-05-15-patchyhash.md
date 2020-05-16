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
```Python
echo -n "9aa2bf82ba045569731de71a5c95463b9297345ea5c6f6f56d29a5e9b6857f47" > shapass.txt
```
