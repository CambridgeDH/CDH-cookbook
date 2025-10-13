<link rel="stylesheet" href="../../cookbook.css">
# Lesson 3: The Mechanics of the Python Language
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents

- [Overview](#overview)
- [Functions: The Building Blocks of Python Code](#functions-the-building-blocks-of-python-code)
- [The Anatomy of a Function](#the-anatomy-of-a-function)
- [Built-in and Preexisting Functions](#built-in-and-preexisting-functions)
- [Function Parameters and Arguments](#function-parameters-and-arguments)
- [Loops](#loops)
- [Summary](#summary)
- [Homework](#homework)

## Overview
In this lesson we will begin writing more complex commands than just naming variables and printing them. By the end of this lesson, you will know the basics of what it takes to accomplish something using Python code!

It is recommended that you feel comfortable running cells in Jupyter Notebooks and that you understand the contents of Lessons 1 and 2 before starting this lesson. Fundamentally, you should know: 

<ol>
<li>How to install and load a Python package or Module.</li>
<li>What a variable is, how to name it, and how to print it.</li>
<li>What data types are, and a few kinds of data types.</li>
</ol>

In this lesson, we will master the most important structure in Python code: the **function**. You will learn what a function is and its 'anatomy'. You will also get your first look at **loops** and will learn to write a simple loop using what you learn about functions.

You are encouraged to follow along by copying and pasting code into your own Jupyter Notebook cells and running them. 

[Back to table of contents](#contents)

## Functions: The Building Blocks of Python Code
In the previous lesson you learned that Python categorises data into different types, such as lists, strings, integers, etc. You also learned how to 'declare' variables by giving your data specific names. But now, we want to *do* something with all of this data. After all, that is the purpose of code: to get the computer to perform tasks for us.

**Functions** are the things that help us do this. They are what we call the instructions telling the computer to do something with your variables. In fact, you have already been using a function: the print statement! This statement is a built-in function (more on that later!) that reads the variable you declared and prints it on the screen.

[Back to table of contents](#contents)

## The Anatomy of a Function
In order to have functions that function, we have to obey the rules of the Python language and use the proper syntax. Functions can be complex or simple, but they all start with a basic core structure. The following function, called 'greet', prints the phrase 'Hello World!' when run:

```python
def greet():
    print('Hello World!')
greet()
```
When looking at code, it helps to break it down into its individual parts. Let's look at this function's parts, line by line.

```python
def greet():
```
'def' tells Python that you are about to **define** a function. 'greet' is the name we will give this function. We could call it anything, but 'greet' makes the most sense here. After 'greet', you see curved brackets, with nothing inside, before a colon. These are where we could put in other elements, called *parameters* to help the function work. But here, 'greet()' doesn't need anything extra, so they are empty. We will explain more about this later in the lesson.

Now, on to the next line:

```python
def greet():
    print('Hello World!')
```
Line 2 here is known as the 'body' of the code. It's indented under the first line because Python follows a **rule of indentation**: anything coming after a colon falls within the instructions for that function, and must be indented under the first line of the function. If I were to write my function like this:

```python
def greet():
print('Hello World!')
```
then my code wouldn't work properly. The unindented line is read by Python as being **unrelated** to the function 'greet'. Usually Notebooks will automatically indent any line after a line ending in a colon (:), but if this doesn't happen, hit the Tab key or four spaces.

Notice also that we see our familiar 'print' statement with the curved brackets. This is where we place the phrase we want to be printed. We could have any phrase we wanted here, such as 'Hi!' or 'What's up?'. 

&#x1F3C1; **Challenge**: Do you know why we have 'Hello World!' in quotes? What type of data is 'Hello World!'?

Now, on to the third line:

```python
def greet():
    print('Hello World!')
greet()
```
Our final line, 'greet()', is like our 'print()' statement. Because we have defined a function called 'greet', we can summon it (or 'call' it) by just writing 'greet()'. Notice that it is isn't indented, and that's because it's not part of the function instructions! We can call greet() anywhere in our program, even in another cell. Try it!

To summarise, the components of a full function:

<ul>
<li>The 'def' statement with the name of the function, and the brackets with a colon.</li>
<li>The indented block of instructions (can be many lines long) </li>
<li>The 'call' of the function later.</li>
</ul>

## Built-in and Preexisting Functions
When you are just getting started in coding, it's not common to write all of your own functions from scratch. If you are using packages or modules that someone else has written, you will often use functions that they have already defined in their code. We will see examples of this in later lessons.

Another very common way that people access functions is by using Python's built-in functions. 'Print' is such a function. We don't have to write the code for instructing the computer how to execute a print action each time, because the code underlying the Python language already has those instructions. You can find a list of all the built-in functions that Python has to offer [here](https://docs.python.org/3/library/functions.html). 

When we use a built-in or preexisting function, we 'call' it. Since our greet function now exists, we can type it in another cell, and run that cell. We have thus 'called' the function. 

[Back to table of contents](#contents)

## Function Parameters and Arguments
As mentioned above, some parts of our greet function have empty brackets, but that's not always the case. There are two concepts to help us understand why: **parameters** and **arguments**.
Parameters are variables which we can put inside of the function definition (where we say 'def function_name():') to tell the function what kind of input to expect when running. Arguments are the specific inputs you provide when you call the function.
Here's an example:

```python
def farewell(name):
    print('Goodbye', name)

farewell('Sarah')
```
In this case, we did three things:

<ol>
<li>We told Python to expect a name as the input. This is the parameter. It acts as a placeholder for any name we give later. </li>
<li>We used that same word, name, inside the body of the function to show where the input should appear when the function runs.</li>
<li>When we call the function, 'farewell('Sarah')', Sarah is the input, or argument. </li>
</ol>

&#x1F3C1; **Challenge**: Change 'Sarah' to a different name. What happens?

Functions can handle many inputs. We can give functions multiple inputs by listing multiple parameters, like so:

```python
def introduction(name, age):
    print("My name is", name, "and I am", age, "years old.")

introduction("Nancy", 55)
```
Here, we gave the function we call 'introduction' two parameters: name, and age. We put them in the parentheses and separate them with a comma.
Notice that the print statement also separates out the components the way we want. When we call the function, all we have to do is specify our arguments: the name, and the age.

&#x1F3C1; **Challenge**: reorder the elements within the print statement, but make sure you have 'name' and 'age' somewhere inside those brackets. What happens when you call the function now?

[Back to table of contents](#contents)

## Loops
The above functions we have written are useful in that they achieve something. But what if we have multiple things to print? Calling the same function over and over, and substituting in different inputs would be tedious.

Fortunately, Python has a specific kind of code structure called a **loop** which can do the work for us. While there are different kinds of loops, the most straightforward is the **for loop**.

A for loop allows us to run the same code over and over, across a list or other collection of data. Here's an example:

```python
patients = ["Alice", "Ramji", "Jonathan"]

for patient in patients:
    print("Hello", patient)
```
When we run this code, we get the word Hello printed with the names of our patients, three times. Let's break down the 'anatomy' of this loop:

```python
for patient in patients:
```
In plain English, this means: "For each patient in the list called patients, do the following:"
Then, in the next line, which we remember **must** be indented, it gives the instructions to finish the sentence: 'print the word Hello, with the patient's name. Do this until you run out of patients.' 

### Loops with Functions
We can combine this with our greet function, too:

```python
patient_names = ["Jeremy", "Rashid", "Lina"]

def greet(patient):
    print("Good morning,", patient)

for patient in patient_names:
    greet(patient)
```
Notice that in the 'greet' function, you can say 'patient', but in the loop, you say 'for patient in patient_names'. This is because you are asking the loop to read the list called 'patient_names' and insert each element (patient) in that list into the greeting. 

[Back to table of contents](#contents)

## Summary
In this lesson you have learned the most crucial elements for getting your code to accomplish something with your variables: writing a function, and getting that function to iterate over multiple pieces of data. Try out the homework exercises below to solidify this knowledge.

[Back to table of contents](#contents)

## Homework
The exercises for this lesson have three levels depending on how much challenge you want:

 <li>Easy: create a list with up to 10 elements. Write a for loop that prints those elements with a meaningful phrase.</li>
 <li>Medium: Make a function that takes two inputs, like a name and a food. Then call the function to print a sentence that makes sense with these two inputs. </li>
 <li>Hard: Search online for a way to find an item in a list using Python code. Write one line of code that prints the second item in your list.</li>


<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="Fundamental-Commands-Python.html">&lt; Previous lesson</a></p>
