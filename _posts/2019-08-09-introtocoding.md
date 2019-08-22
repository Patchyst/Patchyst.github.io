---
title: "Intro to Programming part 1"
date: 2019-08-09
tags: [Python, Coding Bootcamp]
header:
  image: "images/pythonbanner.jpg"
excerpt: "An introduction to the world of programming"
---

## *Which programming language should I learn first?*
While their is a "right" answer to this question, you don't necessarily *have* to start off with this language, if javascript or C++ really grabs your attention then go for it, but if you really just want to build a solid foundation in programming while having the ability to make cool projects you should start learning Python. Just because Python doesn't look as complicated as the other languages doesn't mean its just a *beginner* language that's used for a little while then discarded. Python is an extremely versatile language that is used in everything from programming robots to cybersecurity and ethical hacking. Python's simplicity also eases the weight off of learning all the computer tech jargon that intimidates people. To give you an idea of Python's simplicity compared to other languages:
Printing characters into a console in Python:
```python
print("Hello World")
```
Printing characters into a console in Java:
```Java
public class helloworld{
    public static main void(string[] args){
        system.out.println("Hello World");
    }
}

```
Which one do you think is easier now? One's print function is easy and intuitive while the other's looks like some form of cryptography at first glance. Now don't take this the wrong way you should 100% learn Java at some point. Java isn't actually very hard, Python is just better at dealing with the learning curve that comes with programming.
## *I want to learn to code, but I can't take any classes*
Believe it or not nowadays most programmers start out self taught. Yep, programming offers some of the highest paying jobs and you can *teach it to yourself*. Take Elon Musk for example, when he first founded Zip2 nearly everything he knew about programming was self taught. Zip2 would go on to be sold for 305 million making him rich off of self taught knowledge.
## *Where do I go to teach myself programming?*
I started off on Youtube, udemy, and stack overflow. Udemy courses aren't free, but you can buy professionally made online programming courses for 10-15$. However, there are so many open source, free resources that you really don't need to pay at all, and as you might have guessed I have an intro to Python course that I'm working on. I'll do my best to explain **everything** clearly and completely because it bothers me when someone throws out new terminology that hasn't been explained well and expect you to understand.
## *disclaimer*
The basics of any programming language is **boring**, but once you've learned it you can pretty much jump into any project with a little creativity and ingenuity.
# Running a program in Python
After you've setup and downloaded an IDE to run Python (e.g. Visual Studio Code, Pycharm) and created a file in the proper format you're ready to run your first program. To begin, we'll go over variables they're pretty easy and you've most likely used them a lot in math. A variable can have any datatype assigned to it (I'll go over the basic data types soon.). For example, lets say you want to set a variable equal to an integer it would be as easy as this:
```python
number = 4
```
I could change the "number" variable to nearly anything and it would be still equal to 4. Variables are an essential part of programming and around 30 - 50% of what you're seeing in a program is probably some kind of variable. You can change the value of a variable pretty easily. For example if you wanted to add or subtract from a variable you would do as such:
```python
number = 4
number += 7
number -= 2
```
We just added 7 to the number variable then subtracted 2. That means that the "number" variable should be equal to 9. To test this we would just use the print() function (a function is pre-built in code used to perform specific tasks.) to print out the variable's value in the console screen:
```python
number = 4
# adding 7 to the number variable
number += 7
# subtracting 2 from the number variable
number -= 2
print(number)
```
You should've gotten the output 9. You probably noticed that I put the number variable inside the print() function's parenthesis. Inside the parenthesis is something known as a function's "parameters" this is basically what type of information needs/ or can be passed into the function. In the case of the print function's parameters it will take in any value that can be "printed" into the console window. You could go a step further and create two variables with integer values and assign a variable to an operation done on those two variables:
```python
x = 3
y = 5
# Multiplying x and y and assigning the output to z
z = x * y
print(z)
```
when you print z you should get the output 15.
In case your wondering what I'm doing with the # all it's doing is telling the program to ignore that line of code. Using the # is a common way for programmers working in groups to make notes inside the code about important information or explanations.

# Data types
There are many different data types including integers, strings, floats(called doubles in Java), and MANY MANY more. There are tons of different data types, but I'll just be going over the essential, basic ones for now. An integer is pretty self-explanatory(4), a string is just a collection of characters set using quotes("String"), and a float is a decimal value (4.0). Lets create a few variables with different data types:
```python
string_variable = "Hello World"
integer_variable = 4
float_variable = 4.0
```
All of these are the most common data types you will see. You can change them by using functions like str() which changes the variable to a string and int() which changes the variable into an integer. In case you aren't sure what data type a variable is you can use the type() function inside a print(). Lets change a few variables and check there types:
```python
string_variable = "Hello World"
integer_variable = 4
float_variable = 4.0
# prints the type of the integer_variable being converted to a string
print(type(str(integer_variable)))
# prints the type of the string_variable
print(type(string_variable))
# prints the type of the float_variable
print(type(float_variable))

```
 if all the parenthesis is confusing you think of it as layers, the type function is inside the parameters of the print() and inside the type is the variable. So your finding the type of float_variable type(float_variable) and putting it in the print function so it shows you the result.
Output:
```python
# str is short for string
<class 'str'>
<class 'str'>
<class 'float'>
```
The first is the type of out integer_variable that is being converted to a string, the second is the type of our string_variable, and the third is the type of our float_variable. Another data type that is commonly used is a list. This one is also pretty self-explanatory It's just a list of values.
```python
my_list = [1, 5.7, "string"]
```

This is just a list of random values I created, and if you were to print out the list you would see everything in the list. Usually lists consist of one data type, but for this example I put all the data types we've learned into it. Each value is separated by a comma and each individual value can be changed.
Now we'll cover "concatenation" to concatenate is a technical term which basically means to combine two things. For example we could make two string variables and "concatenate" them.
```python
# notice how I included a space after Hello so that there would be a space when the two variables are combined
string_one = "Hello "
string_two = "world."
# combining the two variables using +
print(string_one + string_two)
```
You should receive the output:
```python
Hello world.
```
The next data type is called "Boolean". (Don't ask me why it's called that) A Boolean can only be one of two things, True or False. And with that we segue into the next topic Conditionals.
# Conditionals (making a password program)
I mentioned Boolean values last on purpose because conditionals are closely related with them. conditional produce True or False depending on the conditions passed in. If False then the program will end if there are no alternative conditionals. You'll see what I mean here in a second. first let's use the input() function all this function does is take in input from the user. The default data type for input() is a string meaning anything the user types into the input will be automatically converted into a string unless instructed otherwise. To begin, lets start off by creating a variable for input called "password":
```python
password = input("Please set a password: ")
```
When the program is run "Please set a password" will appear in the console window and whatever the user types in will be stored in the "password" variable. Create another input variable that asks the user for their password:
```python
password = input("Please set a password: ")
ask_password = input("Enter password:")
```
This is where conditionals come in. The first conditional used is always "if".
```python
password = input("Please set a password: ")
ask_password = input("Enter password:")
if ask_password == password:
    print("Granted")
```
*breaking it down*: After the two inputs are entered the if statement runs and checks to see if the ask_password is equal to whatever value is stored in the password variable. Since we use the "=" operator to assign variables the double equals sign "==" is used to check if one value is equal to another (just like the = sign in math). Lastly, you may be asking "Why is the print statement a few space to the right". This is used to show that the print() function is "associated" with the if statement. Meaning it will only print "Granted" if the If statement's condition is met. Now let's say the user inputs the wrong password, then what? Well, we can use an "else" statement which runs if no other conditionals are True.
```python
password = input("Please set a password: ")
ask_password = input("Enter password:")
if ask_password == password:
    print("Granted")
else:
    print("Denied")
```
If you run this the output might look something like this:
```python
Please set a password: Hello
Enter password:2
Denied
```
Or
```python
Please set a password: 1234
Enter password:1234
Granted
```
Now what if we want another if statement to run after the if statement? Well, this is known as an elif statement and it's basically the same thing as having another if statement. For example add this line of code in between the if and else statements:

```python
password = input("Please set a password: ")
ask_password = input("Enter password:")
if ask_password == password:
    print("Granted")
elif ask_password == "1234":
    print("5678")
else:
    print("Denied")
```
When the program is run it will check if the if statement is true and if not it will move on to the elif statement and check if it is also true. If the elif statement is true than it will run the code that is inside of it. In our case the elif is checking of the ask_password input is equal to the string, "1234". If you run this and enter 1234 for the ask_password input you will get:
```python
Please set a password: PasSworD
Enter password:1234
5678
```
The popular text-based game from 1971, "The Oregon Trail" is based off the same concepts of conditionals. For example:
```python
choice = input("Would you like to A. Swim across the pond, B. Fight the bear, or C. Run")
if choice == "A":
    print("You died")
elif choice == "B":
    print("You fight the bear and win")
elif choice == "C":
    print("You died")
else:
    print("Invalid Input")
```
This is just an example and to make a full game you would need a bit more, but I'll cover it all in part 2. Hopefully, you found this informative and if you think I need to change or fix anything you can [email](https://patchyst.github.io/about/) me.
