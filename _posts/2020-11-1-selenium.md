---
title: "Automating Web Activity with Selenium"
date: 2019-08-20
tags: [Advanced Projects,Python]
header:
  image: "images/tensor.jpg"
excerpt: "Use Python's Selenium library to automate web activity"
---
Selenium's [documentation](https://selenium.dev/documentation/en/) defines the Selenium library as "an umbrella project for a range of tools and libraries that enable and support the automation of web browsers". The Selenium WebDriver receives commands from a broad range of programming languages (I.g. Java, javascript, Python C#, R) and uses them to manipulate browser behavior. Begin by importing Selenium's WebDriver object and functions:

```python
from selenium import webdriver
```
Selenium's WebDriver is compatible with the following browsers: Firefox, Internet Explorer, Safari, Opera, Chrome, and Edge. For this project I'll be using a Chrome's WebDriver which can be downloaded [here](https://sites.google.com/a/chromium.org/chromedriver/). Once you have the WebDriver installed, create a variable for the WebDriver that specifies what browser you're using with the path to your WebDriver (insert your path in place of mine):
On mac it will look something like this :  
```python
from selenium import webdriver
web_driver = webdriver.Chrome("/Users/patrick/Desktop/chromedriver")
```
On Windows be sure to create a raw string (add "r" before the string) otherwise the backslash will create unwanted escape characters:
```python
rom selenium import webdriver
web_driver = webdriver.Chrome(r"C:\Users\pteds\Desktop\Selenium\chromedriver.exe")
```
Running the code so far should produce a blank page with a banner notifying you that chrome is being controlled by automated test software:

![WEBDRIVER-EX1](/images/chromdriver.png){:class="img-responsive"}

Next use the web_driver variable's function, get(), to pull up the webpage you wish to automate activity or scrape data from:

```python
from selenium import webdriver
web_driver = webdriver.Chrome("/Users/patrick/Desktop/chromedriver")
web_driver.get("https://selenium.dev/")
```
Next access the website's Elements and find the element you wish to interact with:

 ![WEBDRIVER-EX1](/images/webdriver2.png){:class="img-responsive"}
