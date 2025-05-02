<link rel="stylesheet" href="../../cookbook.css">
# Lesson 2: Fundamental Commands and Actions in Python
<p class="previous-next-lesson"><a href="toc.html">^ Main contents</a></p>
## Contents
- [Overview](#overview)
- [Navigating Jupyter Notebooks](#navigating-jupyter-notebooks)
- [Getting Python to Read Data](#getting-python-to-read-data)
- [Loading Packages and Preparing our Data](#loading-packages-and-preparing-our-data)
- [Types of Data in Python](#types-of-data-in-python)
- [Navigating Python](#navigating-python)
- [Lesson Summary](#lesson-summary)

## Overview
In this lesson we will study the following fundamental aspects of dealing with data in Python:

<li>Loading data into Jupyter Notebooks or Google Colab.</li>
<li>How to declare variables.</li>
<li>Good practices for naming variables (very important!).</li>
<li>Types of data in Python.</li>

We will also cover some helpful aspects to navigating Python code such as zero-indexing, comments, print statements, and Jupyter notebook shortcuts.

If you are a beginner at coding, it is important to clearly understand these concepts, because they are integral to how Python operates. If you have some coding experience, this lesson can serve as a review of important fundamentals.

[Back to table of contents](#contents)

## Navigating Jupyter Notebooks
The first step to setting up a coding workspace is to launch Jupyter Notebooks, and create a new notebook for yourself. If you did the homework in the last lesson, then you initiated a Notebook and typed some commands into some cells and ran them. Here we will take a closer look at the components of a Jupyter Notebook:

[Screenshot with components indicated]
<li><strong>Moving, Cutting, and Running Cells</strong>: Jupyter Notebooks are made up of individual cells. Using the options in the menu at the top, you can move cells up and down, you can 'cut' (delete), or 'add' a new cell, and you can run the code in the current cell. If you run code in one cell which affects cells below it, they have to be run in order (or the computer will not know that the previous cell is relevant). You can reorder cells by clicking the up and down arrows in the menu.</li>
<li><strong>The Kernel</strong>: you can think of this as the 'working memory' of your notebook. If your code gets messy, or you start getting odd results when you run cells, you can restart the kernel by selecting from the restart options in the dropbox. Note that doing this will wipe the memory of the notebook and you'll have to run all your commands from the beginning.</li>
<li><strong>Switching between Code and Markdown</strong>: The cells can either be code cells (which run live code), or they can be Markdown cells (Markdown is a kind of text formatting language for display). To turn a code cell into Markdown, press Control + M, and the cell outline should turn blue. To turn a Markdown cell into code, press Control + Y, and the cell outline should turn blue.</li>


&#x1f4a1; Tip: A full tutorial on Jupyter Notebook shortcuts can be [found here.](https://towardsdatascience.com/jypyter-notebook-shortcuts-bf0101a98330) These shortcuts typically work for most Jupyter-based Notebooks (such as Google Colab), but there are some variations.

[Back to table of contents](#contents)

## Getting Python to Read Data
There are two main ways to have the Python read data. 

### Declaring a Variable
The simplest way is to tell Python directly what data you have. This is known as 'declaring a variable'.

Let's say I have a sentence I want to analyse: 'The lizard slithered through the green grass.' You will need to tell the computer that this sentence exists, and give it a name:

```python
slither_text = 'The lizard slithered through the green grass.'
print(slither_text)
```
What we have done here is given our sentence a name, 'slither_text', and told the computer that it can find the sentence by this name. You can declare anything as a variable, for example:

```python
cat ='Molly'
age = 1000
print(cat)
print(age)
```
Notice the lines that start with 'print'. These are known as 'print statements'. I have told the computer to print the variable I declared. You can try this yourself in a Jupyter Notebook code cell and see what happens. You don't need to print your variables, but it can be helpful to see them. Notice also that variable names aren't capitalised here. While it is allowed to capitalise variable names, this is typically not done because then you must remember that the variable name is capitalised later when you are re-using the variable. It's much easier to just avoid capitalising any variable name. Keep them simple, specific, and descriptive!

Also note that if your text has multiple lines, you can enclose it in triple single quotes (''') or triple double quotes ("""). This allows the string to be easily displayed with line breaks:

```python
multiple_line_text = '''Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum ornare bibendum magna, eu placerat sem. Pellentesque suscipit dolor et est auctor blandit. Mauris lacinia libero quis sem laoreet porta. Nulla vulputate purus mi, vel auctor leo volutpat nec. Phasellus placerat lorem magna, sed porta ante finibus quis. In hac habitasse platea dictumst.'''
print(multiple_line_text)
```

### Reading Files into the Workspace
Another way to bring in your data is to tell Python to read a file. Jupyter Notebooks uses your home file as its 'working directory', and can read any files within it. Let's put a text file (.txt format) called 'slither_text' into your working directory, with the sentence we had up above: 'The lizard slithered through the green grass'. Then we will run this code:

```python
slither_file = open('slither_text.txt')
print(slither_file.read())
```
This code creates an object called 'slither_file', which is opened and read by the built-in functions 'open' and 'read'. We first ask it to open the file (using the filename with single quotes) and save it as the object called 'slither_file'. Then we ask it to read and print the contents of the slither_file object.

Note that if your data is in an Excel spreadsheet, there are various Python modules and tutorials out there which are designed to make importing and reading spreadsheets in your Python workspace very easy. 

&#x1F3C1; **Challenge**: can you find a tutorial online that tells you how to import an Excel spreadsheet into your workspace using a Python package or module?

[Back to table of contents](#contents)

## Loading Packages and Preparing our Data
For this lesson and the next, we are going to use the packages 'textblob', 'nltk', and the module 'os' to play with some text analysis. So, ensure your Notebook is ready to go, and let's install and import these packages and modules. Copy and paste the following code into the first cell:

```python
%pip install textblob
%pip install nltk
# These two lines will install two packages on your hard drive.
# We do not need to install 'os' because it is a built-in Python module.

import nltk
import textblob
import os
# These lines will import the two packages you just installed.
# Note that we also import the built-in Python module.  

from textblob import TextBlob
# This line imports a specific Class of commands, TextBlob, from the textblob package
# Notice the capitalisation for the difference!
# While we don't typically capitalise variable names, Class names are sometimes capitalised.

```
Now that we have installed and loaded all the necessary software, in order to do anything with it, we next must declare a variable:

```python

orwell_text = '''It was a bright cold day in April, and the clocks were striking thirteen.
Winston Smith, his chin nuzzled into his breast in an effort to escape the
vile wind, slipped quickly through the glass doors of Victory Mansions,
though not quickly enough to prevent a swirl of gritty dust from entering
along with him. The hallway smelt of boiled cabbage and old rag mats. At one end of it a
coloured poster, too large for indoor display, had been tacked to the wall.
It depicted simply an enormous face, more than a metre wide: the face of a
man of about forty-five, with a heavy black moustache and ruggedly handsome
features. Winston made for the stairs. It was no use trying the lift. Even
at the best of times it was seldom working, and at present the electric
current was cut off during daylight hours. It was part of the economy drive
in preparation for Hate Week. The flat was seven flights up, and Winston,
who was thirty-nine and had a varicose ulcer above his right ankle, went
slowly, resting several times on the way. On each landing, opposite the
lift-shaft, the poster with the enormous face gazed from the wall. It was
one of those pictures which are so contrived that the eyes follow you about
when you move. BIG BROTHER IS WATCHING YOU, the caption beneath it ran.'''

# This command takes a passage from a text and gives it a name, 'orwell_text'.
# Note that we have enclosed it in triple single quotes so that it will display nicely for us.

```
Now we have everything set up: our packages and modules are installed and loaded, and we have some data with which to work. But before we start doing things, it is important to understand what 'data' means to Python. Go ahead and save your Jupyter Notebook with a memorable name, as we will return to it in this lesson as well as later lessons.

[Back to table of contents](#contents)

## Types of Data in Python
Just as we work with different kinds of data in everyday life, so Python has different ways of categorising data, which are known as 'data types'. It is important to know what these are and how to tell Python which data type you are using,  because certain programming operations will only work with particular data types. We will learn a few of the fundamental types today. In your Notebook cells, work through the examples below by copy and pasting the code and then running the cells.

### Strings
Strings are lines of continuous text, like our test sentence above.
In Python, we declare a string variable by ' ' (or by the triple quotes discussed above):

```python
slither_text = 'The lizard slithered through the green grass.'
print(slither_text)
type(slither_text)
```
If you run the above code in a cell, you will find that Python prints the type of data that 'slither_text' is, which is what we call a 'string'. It abbreviates this as 'str'. Any combination of letters is a 'string'.

### Numeric Variables
Unlike strings, numeric variables don't need special formatting to be declared:

```python
age = 1000
print(age)
type(age)

weight = 111.5
print(weight)
type(weight)
```
Note that there are different kinds of numeric variables, these two examples are for the 'integer' and 'float' types.

### Sets
A very common data type in Python is a set. The Python language defines a set as an **unordered** sequence of specific and **unique** things.

```python
snake_types = {'python', 'anaconda', 'rattlesnake', 'garden'}
print(snake_types)
type(snake_types)

# The order in which Python prints the sets is arbitrary.
# Note that if I change the order of the elements in the set, nothing happens:

snake_types = {'anaconda', 'rattlesnake', 'python', 'garden'}
print(snake_types)
```

### Lists
Lists appear similar to sets, but are computationally distinct. They are an **ordered** sequence of things, but they do not need to be unique. They are modifiable, or 'mutable' (you can reorder or add or remove elements). They are made with square brackets:

```python
Breeds = ['Arabian', 'Clydesdale', 'Thoroughbred', 'Friesian']
type(Breeds)
print(Breeds)

# And you can change an element in the list like so:
Breeds[2] = 'Standardbred'
print(Breeds)

# Now, in a new cell, type this:
Breeds = ['Standardbred', 'Arabian', 'Standardbred', 'Thoroughbred', 'Friesian']
print(Breeds)

# Can you describe what happened?
# Remember that lists do not need to have only unique elements. Things can repeat.

```

&#x1F3C1; **Challenge**: Add in a duplicate to your code on the set of snakes (snake_types). Print it. What happens differently if you print a set with a duplicate item?

### Dictionaries
Dictionaries are organisations of data into 'keys' and 'values'. These terms come from database design and programming. Essentially, a key is an entry for an object in the dictionary, and the value is something which describes the key. Below I have a group of horse breeds, the keys. Each breed of horse has a name, the value:

```python
My_Horses = {
    "Arabian": "Alex",
    "Clydesdale": "Scotty",
    "Thoroughbred": "Speedy",
    "Friesian": "Prince"
}
print(My_Horses)

# In a new cell, to get the type of data we have:
type(My_Horses)

```

While these examples of data types may seem trivial now, when you start coding actual commands or doing real data analysis in Python, they will immediately become relevant. Here is a summary table of these types:

| Data Type   | Syntax Example                            | Key Features                              |
|-------------|-------------------------------------------|--------------------------------------------|
| `str`       | `'Hello'`, `'''Multi-line text'''`        | Text data, uses quotes or triple quotes |
| `int`       | `42`                                      | Whole numbers                             |
| `float`     | `3.14`                                    | Decimal numbers                            |
| `list`      | `['a', 'b', 'c']`                         | Ordered, changeable (mutable), allows duplicates |
| `set`       | `{'a', 'b', 'c'}`                         | Unordered, unique elements only         |
| `dict`      | `{'key': 'value'}`                        | Key-value pairs to describe structured data |



[Back to table of contents](#contents)

## Navigating Python
Finally, here are a few aspects of Python which are essential for coders to know:

### Python is zero-indexed!
What does this mean? When Python is asked to count something, it starts at 0, not 1. Therefore, the 0th letter of the English alphabet is A, and the 1st letter is B, etc. If you need to find the 16th item in a list, for example, knowing this fact is helpful!

### Comments are your friend
You will have noticed that I made a lot of comments in the code examples in this lesson. I also mentioned in the previous lesson that comments are helpful and to not be afraid to write them. You can see how helpful they are! Note that you can also use comments to 'turn off' lines of code in a program that you don't want to run. Comments are, as some people put it, a gift to your future self, so use them!

### Print statements are also your friend
As we will see in the following lessons, print statements are extremely useful. They can be the main outcome of a function, or they can be used to ensure your code is working properly in the background. You can use print statements to clarify your code, to make outputs easier to read, and more. 

### What you name your variables is really important
When you're in the midst of analysing data, and creating multiple variables in a group of commands in your code, you will want your variable names to make sense. The rule of thumb is to keep your variables short but descriptive and specific. Some people have the habit of calling their variables things like 'x', 'y', or 'variable1', 'variable2', etc. This is a bad idea for two reasons: 
<li>When you come back to your code later, you may not remember what the variable was supposed to signify</li>
<li> Badly-named variables can be easily overwritten later, which means that you can accidentally name two different things the same name. The computer will only use the latest declared variable, so if you have x = 'Cat' and later write x = 'Dog', the computer will only read 'Dog'.</li> 
You can see how not being specific and careful with variable names can create problems!

[Back to table of contents](#contents)

## Lesson Summary
In this lesson we have covered the following core concepts: 
<li>The basics of navigating Jupyter Notebooks</li>
<li>What variables are, and how to 'declare' them</li>
<li>How to tell Jupyter Notebooks to read files from your home folder</li>
<li>What data types are and their importance to coding in Python</li>
<li>Essential facts about Python</li>


 In the next lesson we will cover functions and for loops, which is fundamental syntax for doing tasks in Python. Before going there, you should practice some of these skills by working on the homework exercises below.

 [Back to table of contents](#contents)
 
## Homework: 
1. Search online and read about the textblob package. 
2. Create some new variables for textblob to read directly in Jupyter Notebooks. Print them and ask Python to tell you what data type they are.
3. Create a .txt file in your home folder ('working directory') and load it into your Jupyter Notebook workspace. 
4. Search online about how to change your working directory in Python, and give it a try.

**Reflection**: Think about some data you recently needed to analyse. What would you need to do in order to load it into a Python workspace? Could you store some of your data as strings, lists, sets, or dictionaries? Why a given type? How does thinking about your data in the framework of a 'data type' change your perspective on your data?

<p class="credits">Written by Estara Arrant, 2025-04-16<br />Licence: <a href="https://creativecommons.org/licenses/by-sa/4.0/">CC BY-SA 4.0</a></p>

<p class="previous-next-lesson"><a href="Introduction-Python-Language.html">&lt; Previous lesson</a> | <a href="Mechanics-Python-Language.html">Next lesson &gt;</a></p>
