---
title: "Automating Web Activity with Selenium"
date: 2020-01-01
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

Next use the web_driver variable's function get() to pull up the webpage you wish to automate activity or scrape data from. Access the website's html and find the element you wish to interact with::

```python
from selenium import webdriver
web_driver = webdriver.Chrome("/Users/patrick/Desktop/chromedriver")
web_driver.get("https://patchyst.github.io/")
```


 ![WEBDRIVER-EX1](/images/webdriver2.png){:class="img-responsive"}

 Selenium offers a variety of methods for finding the target element, each of which are used in specific cases. Elements can be located by ID, name, class name, tag name, link text, CSS selector, and XPath. Because I don't have an easy way of finding my element, I'm using xpath which uses an XML path expression to locate elements on a web page. Finally store the element in a variable (make sure you aren't using the plural form of element or a list will be returned):

 ```python
 from selenium import webdriver
 web_driver = webdriver.Chrome("/Users/patrick/Desktop/chromedriver")
 web_driver.get("https://patchyst.github.io/")
 target_element = web_driver.find_element_by_xpath(r'//*[@id="site-nav"]/ul[1]/li[1]/a')
 ```
 Now that the target element has been found and stored in a variable it can be interacted with. Selenium has functions for interacting with everything from text boxes to drag and drop boxes, but for **now** lets keep it simple and click on the element (be sure to close the driver when the program is finished):

 ```python
 from selenium import webdriver
 web_driver = webdriver.Chrome("/Users/patrick/Desktop/chromedriver")
 web_driver.get("https://patchyst.github.io/")
 target_element = web_driver.find_element_by_xpath(r'//*[@id="site-nav"]/ul[1]/li[1]/a')
 target_element.click()
 web_driver.close()
 ```
 In my case, the element was a link, so the webpage immediately redirected to the page.
