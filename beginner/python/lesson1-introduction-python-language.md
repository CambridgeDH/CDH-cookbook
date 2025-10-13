# Lesson 1: Introduction to the Python Language
<link rel="stylesheet" href="../../cookbook.css">
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents

- [Overview](#overview)
- [Setting Up Your Workspace](#setting-up-your-workspace)
- [The Difference between Coding and Programming](#the-difference-between-coding-and-programming)
- [Immediate Goals and Four Fundamental Principles](#immediate-goals-and-four-fundamental-principles)
- [The Structure of Python Programs](#the-structure-of-python-programs)
- [Getting Acquainted with Python Packages and Modules](#getting-acquainted-with-python-packages-and-modules)
- [Code Repositories](#code-repositories)
- [Essential Resources for Learning to Code](#essential-resources-for-learning-to-code)
- [Lesson Summary](#lesson-summary)
- [*Homework*: Exploring Python Programs](#homework-exploring-python-programs)

## Overview
Welcome to the course First Steps in Coding with Python. This is the introductory lesson to the course, and if you are new to Python or to coding, this lesson will give you some fundamental concepts to carry with you as you learn to code in this language. This lesson covers:

<ul>
<li>Conceptual differences between 'coding' and 'programming'.</li>
<li>The general way most Python code is organised.</li>
<li>How to install and load Python source code into your workspace.</li>
<li>What code repositories are and how to navigate them.</li>
<li>Some essential resources to help you as you learn to code. </li>
</ul>

[Back to table of contents](#contents)

## Setting Up Your Workspace
In order to understand the content of this lesson and do the exercises at the end, you will need to either have Anaconda installed and be able to launch Jupyter Notebooks, or be able to access Google Colab. You will also need to know how to find your 'home folder'. For instructions on these matters, see [LINK] in the Prerequisites section of the Cookbook. 

[Back to table of contents](#contents)

## The Difference between Coding and Programming
In this course you will learn how the Python language works and how to write Python code. Code is the building material for computer programs, which are complex sets of instructions that guide the computer in performing specific tasks. When starting out on working with code, it can be helpful to distinguish between the concepts of 'coding' and 'programming': 

### Coding
In 'coding', the focus is on using the principles of how a language works to write specific commands that a computer can correctly interpret. In order to code you must understand these principles and how to translate them from human concepts into the right digital format, or 'syntax'. Someone who is 'coding' is writing lines of computer instructions. Essentially, learning to code is learning how to make the bricks out of the clay that is a programming language.

### Programming
'Programming' involves not only writing individual commands but putting them together into more complex components to achieve sets of tasks. It incorporates planning a computer program and putting the pieces together seamlessly, as well as ensuring they work well and that they remain useable over time. If coding is like making bricks, then programming is like creating a building out of those bricks. However, at the heart of programming is good-quality code.

[Back to table of contents](#contents)

## Immediate Goals and Four Fundamental Principles
No matter whether your goal is to become a full-fledged programmer, or to simply write some code for your particular project, the aim is the same: learn to read and write sensible, legible, and functioning code, and know how to handle a code situation that has gone wrong. That is the focus of this course.

It is easy to become overwhelmed when confronted with large, complex programs that other people have written, and it is easy to feel disheartened when one's simple command doesn't work. To help, keep in mind these four fundamental principles that all Humanists who write code need:

<details>
<summary>&#x1f4a1; Fundamental Principles for Learning to Write Code (expand)</summary>
<ol>
<li>Focus on the practical matters. When coding, keep the focus on the concrete idea of what you are trying to achieve in the moment. Aim to think as practically as possible.</li>

<li>Break things down into their smallest possible components. Coding is a detail-heavy process where one can easily lose track and become overwhelmed. Good coders 'chunk' their learning, writing, and thinking into small bits, and focus only on the bit with which they are working at the time. A bit of mindfulness goes a long way here!</li>

<li> One of the most important skills for any coder to have is the ability to search the internet for solutions to the problems that one encounters (and you will encounter problems!). This skill is more important than knowing tons of facts about a language, since there will always be things you do not know or cannot remember.</li>

<li>Coding is a skill: learning concepts about how Python works is necessary, but not sufficient. Think of learning to code as similar to learning to speak a language: it demands actual practice, and the more you do, the better you will become at it. Make a habit to do a bit of coding daily as you learn, even if your goal is only to write something very simple.</li>
</ol>
</details>

### Using ChatGPT or other Generative AI Tools
Today, as AI tools are becoming ubiquitous, it is natural that you may want to turn to these tools for assistance to help you learn to code. This is a generally good strategy, but there is the risk of over-relying on these tools and then not truly learning the material. Most programmers use AI as a **tool**, or an assistant, to help them write good code, rather than a means of producing code directly. Here are my **top three tips** for integrating AI into your learning process appropriately:

<li>1. Ask questions for the AI to answer, don't ask it to do tasks for you. Coding is a skill: you will not learn unless you practice it yourself. But asking AI to help you understand coding concepts or to help you figure out the components of your code is very useful for learning. </li>
<li>2. Don't blindly rely on code that the AI generates. Typically, the code it writes is twice as complex and half as effective as the solutions that you will encounter in this course. A better use of AI is to paste someone's code into the chat and ask it to explain the code for you, or to ask it to help you think through the steps of a problem.</li>
<li>Use the AI tool to push you deeper into understanding, not to automate understanding. It feels tempting to ask it to explain something to you the moment you feel a bit frustrated, but that frustration is actually your brain making new connections. Try to think through a question or problem first, and then use the AI to see if you missed anything after.</li>

In summary, AI platforms like ChatGPT can be powerful tools to assist your learning, so long as you use them with discretion and always prioritise doing the activities yourself and thinking through isses and concepts first before turning to it for help.

[Back to table of contents](#contents)

## The Structure of Python Programs
One way that many people gain coding experience is by using and modifying code that others have already developed. In order to do this, it is important to understand how computer programs written in Python are structured.

A common way of organising Python code is to put it into a 'package' - a collection of components that work together to perform a major task, made up of multiple, specialised code files known as 'modules', with filenames that end in .py. While modules are often part of a package, they can also stand alone. Modules typically contain functions: pieces of code which perform very specific tasks. Functions do this by using variables, which are the names that we give to specific pieces of data involved in these tasks. 

A metaphor might help us here:

Think of a big organisation, like a large library that has multiple buildings, each dedicated to housing books on a particular subject. The library is akin to a **'Package'**, and each building is a **'Module'**. Let's say that this multi-building library is called 'The History of the Entire World', and I'm a library reader who wants to study Early Modern History. First I need to find the module for Early Modern History, but once I've gotten to the building, there are still more components that I need to work through. 

When I enter the Early Modern history module, I find that it has multiple floors dedicated to the history of different areas of the Early Modern world. These floors are akin to what we call **'Classes'** in our program: Classes break up the complex instructions of code into meaningful sub-units. Let's say I am particularly interested in the Early Modern history of India - so I travel to that floor (Class). In this India 'Class' are many even smaller sub-units: individual books, all dedicated to very specific areas of the history of Early Modern India. These books are akin to what we call **'Functions'** in our program - Functions are the blocks of code that contain commands. Without them, our library would be very empty indeed! 

Suppose a particular book on Mumbai catches my eye. I open it up, and find that it has chapters and subsections. These are the **'Variables'**, or the pieces of data which the function uses to complete a task - in this case, to describe the history of Early Modern Mumbai. Not all chapters look alike: some are long, some are short. But they all have one thing in common: they deal with **'Data'** about Early Modern Mumbai. Some of these data are lists, and some are descriptions, numbers, etc. Such data types -- organisations of data into particular formats - make up the unique features of this book. 

&#x1F7E9; This metaphor is of course simplified in order to help you conceptualise how most Python code is typically organised, but know that actual Python programs are not always so neatly structured, and each component can exist on its own or in combination with other components, for example a Module can exist independently of a Package, and we can use Functions by themselves. 


[GRAPH OF THE PYTHON STRUCTURE?]

[Back to table of contents](#contents)

## Getting Acquainted with Python Packages and Modules 
We are going to work at the Package and Module level for now. One of the best places to find Python packages is the [Python Package Index](https://pypi.org/). Most packages are developed by software developers and are often open-source, which means that they are produced by individuals or a community and are publically available for free use. 

### Installing and Importing Packages
In order to install packages, you need Python's built-in installer, known as 'pip' (short for 'Pip Installs Packages'). If you are using Jupyter Notebooks or Google Colab, pip is usually pre-installed on those systems, so you can use it right away to install packages. Let's install a package to see how it works.

Type the following command into a Notebook cell and hit 'run': (Note: you will need to scroll to the side to see the entire text within the code block. This is common in Notebooks.)

```python
%pip install textblob
# This command will tell Python to install the package 'textblob' on your computer. This package has Natural Language Processing programs.
```
&#x1f4a1; Depending on the Notebook, you might need to use !pip instead of %pip; these are roughly equivalent.

&#x1f4a1; See the text following the hashtag ('#') in the code snippet above? That is known as a 'comment', and anything following the hashtag sign is a freeform language comment written by the coder. Writing comments can be a helpful way to explain your code to your future self or to others. Don't be shy about writing comments!

**To summarise**: the syntax (programmer-speak for 'correct format') for installing a package is:

```python
%pip install <package_name>
# Note that you don't need '' or < > around the package name.
# Also, when you see < > around something, it usually indicates free text.
# For example, if the package name was 'interestinggadget', you'd substitute it for <package_name> like so: %pip install interestinggadget. 
```
That is usually all you need to install a package on your machine if you've typed the package name correctly. If the package is already installed on your computer, you will get a message that explains this. To double check if you have your package successfully installed, run the following:

```python
import <package_name>
```
If the package is installed, nothing special should happen, and the Notebook should move you down to the next cell. If it is not installed, you will get an error message. Note that to use a package which you have installed, you will always need to import it, using the above import command, each time you run your program. We typically put all import and install commands at the top of a program for convenience. 

&#x1f4a1; For those interested, [this](https://python.land/virtual-environments/installing-packages-with-pip) is a more in-depth look at pip and installing packages on your computer.

### Importing Python's Own Modules
In addition, you also have access to many modules that come with Python, collectively known as the Python Standard Library. You do not need to install these separately. These modules are used in nearly every package you will encounter, so it is useful to know how to find and use them. The contents of the Python Standard Library are found in the [Python Module Index](https://docs.python.org/3/py-modindex.html). Just like packages, you can import these modules with the following syntax:

```python
import <module_name>
```
### Importing Specific Components within Packages
Sometimes, however, you may only need a specific element (such as a class or a function) rather than the entire module or package. If you have installed a package or imported a module and you know the specific component that you want to use, you can run the following command:

```python
from <module_name or package_name> import <component_name>
# So, let's say I am working with Python's built-in difflib module and I want to use its SequenceMatcher class. 
# I can do this like so:

from difflib import SequenceMatcher
```
Again, nothing happens visibly with this command. If you don't get any message, that means the import succeeded.

[Back to table of contents](#contents)

## Code Repositories

Now that you know how to access packages and modules on your machine, it is time to become (generally) acquainted with the repositories where the vast majority of the world's code is stored. [Github](https://github.com/) is a central place where developers will host their code for others to access. Anyone can have a repository, and most open-access code is hosted here.

First, let's look Python's own [repository](https://github.com/python/cpython/tree/main). 
Below the list of folders you will find a ReadMe file displayed. Every good repository has a ReadMe placed for users to see that gives important information about the repository. 

Now, look for the 'Lib' folder. Here you will find a list of all the code components. Find the folder for the module named 'difflib' and click on it. There you will see the source code for the entire module. This source code is also displayed in human-readable format [here](https://docs.python.org/3/library/difflib.html?fbclid=IwAR23PpxJ0wGFXAGFdKD5U5cgtukFRmk-m5BwQe16I-keGEXJIbbUgEi0gsI#difflib.Differ). The Python repository is huge, because Python is a massively-used language worldwide. 

Next, let's take a look at the (much smaller) repository for the independently developed package we installed earlier: [TextBlob](https://github.com/sloria/TextBlob). 

&#x1F3C1; **Challenge**: Can you find the source code? Can you find the ReadMe and license?

&#x1f4a1; An important point to keep in mind is that GitHub repositories are for code in all programming languages, not just Python! To check if a repository which interests you uses Python, look on the right-hand side, under 'Languages'.

[Back to table of contents](#contents)

## Essential Resources for Learning to Code
Besides accessing packages and their components, there are also important resources to assist you in learning about and writing code. Here are some of the most essential:

- [Github](https://github.com/): The central place for the vast majority of open-source code in existence.
- [StackOverflow](https://stackoverflow.com/): A forum for posting questions about code. Note that StackOverflow has very strict formatting criteria to ensure quality standards. [This](https://stackoverflow.com/help/how-to-ask) is a guide on how to ask questions on StackOverflow successfully.
- [Python's main site](https://www.python.org/)
- [Programming Historian](https://programminghistorian.org/) is a site which hosts articles and tutorials on how to use code for various Digital Humanities tasks. An indispensible resource for the digital humanist.
- [Data Foundry](https://data.nls.uk/) is a site hosted by the National Library of Scotland which provides extensive open-source datasets on a wide variety of subjects and in many different formats -- great for getting datasets to test out methods.

There are many tutorial websites out there as well, and here are a few (note that they are often geared towards a more STEM audience):

- [DataCamp](https://www.datacamp.com/)
- [CodeAcademy](https://codeacademy.com)
- [RealPython](https://realpython.com/)

If you're the kind of learner who likes books, [this](https://pythonbooks.org/free-books/) is a site which lists some popular and helpful Python books for various skill levels (my favourite is *Learn Python 3 the Hard Way*, as it is a complete immersion course into the language).

[Back to table of contents](#contents)

## Lesson Summary
In this lesson you have learned the fundamentals about how Python code is structured, how to install and import packages and modules, places to find open-source code, and some essential resources to support you as you learn to code. In the next lesson we will cover loading data into our codespace, what kinds of data we might have, how to create and name variables, and important tips for navigating Python code. Before you go to the next lesson, try to solidify what you learned by doing the exercises below!

[Back to table of contents](#contents)

## *Homework*: Exploring Python Programs
<ul>
<li>1. Find a few examples of Python packages relevant to Digital Humanities by doing a search online.</li> 
<li>2. Load up a workspace in a Notebook and install one of these packages.</li>
<li>3. Have a look at the built-in modules listed in the Python Module Index, and explore some of what they can do.</li>
<li>4. Look for an interesting tool/module/method on your own and investigate it.</li>
</ul>

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="Fundamental-Commands-Python.html">Next lesson &gt;</a></p>
