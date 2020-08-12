---
title: "Introduction to Keyboard Injectors with Rick Astley (UNFINISHED)"
date: 2020-02-11
tags: [Advanced Projects, Bash]
header:
  image: "images/maltronix.jpg"
excerpt: "Use a Malduino to launch a Rick Roll bomb on an unattended computer"
---



# DISCLAIMER:
Code in this project utilizes your browser for purposes it was not intended for and could potentially damage computer hardware if used excessively. Do not plug a bad USB into any computer without the proper permissions from its owner.


## Bad USBs:
Computers, printers, external drives, scanners, and cameras, they all have one thing in common, a Universal Serial Bus(USB) socket. conveniently, nearly every one of these devices has no security measures in place to prevent harmful devices from being plugged in, the operating system essentially allows the USB to do whatever it wants because anti-virus software cannot access the software on a USB. A "Bad USB" is a USB drive with the microcontroller's firmware reprogrammed in such a way that allows it to be used for malicious purposes.


## Keyboard Injectors
A Keyboard injector is a Bad USB programmed to initiate keystrokes at superhuman speeds once plugged in.

![Keyboard-Injector](/images/injector.gif){:class="img-responsive"}

One such device is the [Malduino](https://maltronics.com/collections/malduinos) by Maltronics. As the name suggests the Malduino is a "bad" Arduino setup using [Arduino's IDE](https://www.arduino.cc/en/main/software).

The Malduino Elite has 4 switches corresponding to binary values 1 and 0. Depending on the switch combination a particular script will execute. I.g. 1010.txt for gaining a reverse shell and 1110.txt for DNS poisoning.  
![malduino](/images/malduino_img.jpg){:class="img-responsive"}
The Malduino uses a scripting language called ducky script (lines are executed successively). 
